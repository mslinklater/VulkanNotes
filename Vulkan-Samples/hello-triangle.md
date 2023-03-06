# Hello triangle

*source:* samples/api/hello_triangle/hello_triangle.cpp

---

## **Data Structures**

### Context

|Type|Description|
|---|---|
|VkInstance|The Vulkan instance|
|VkPhysicalDevice|The chosen physical device|
|VkDevice|The logical device|
|VkQueue|The device queue|
|VkSwapchainKHR|The swapchain|
|SwapchainDimensions|The swapchain dimensions. Size and VkFormat|
|VkSurfaceKHR|The surface to render to - supplied by the platform|
|int|Graphics queue index|
|vector of VkImageView|Swapchain image views|
|vector of VkFrameBuffer|Swapchain image view frame buffers|
|VkRenderPass|The render pass|
|VkPipeline|The render pipeline|
|VkPipelineLayout|The render pipeline layout|
|VkDebugReportCallbackEXT|Debug callback stuff|
|vector of VkSemaphore|Recycled semaphores|
|vector of Per-Frame data|see Per-Frame|

### Per-frame

|Type|Description|
|---|---|
|VkDevice| The logical device - why store it here ? |
|VkFence|Queue submit fence|
|VkCommandPool|Command pool|
|VkCommandBuffer|Command buffer|
|VkSemaphore|Swapchain acquire semaphore|
|VkSemaphore|Swapchain release semaphore|
|int|Queue index|

---

## **Pseudocode**

### Constructor()

### Prepare()

* init_instance
	* validate_extensions
	* validate layers
* init_device
	* validate extensions
* init_swapchain
	* init_per_frame * n
* init_render_pass
* init_pipeline
	* load_shader_module triangle.vert
		* find_shader_stage
	* load_shader_module triangle.frag
		* find_shader_stage
* init_framebuffers

### Update()

* acquire_next_image
* if window resize
	* **resize**
	* acquire_next_image
* render_triangle
* present_image
* if window resize
	* **resize**

### Resize()

* teardown_framebuffers
* init_swapchain
	* teardown_per_frame * n
	* init_per_frame * n
* init_framebuffers

### Destructor()

* teardown
	* teardown_framebuffers
	* teardown_per_frame * n

---

## **Methods**

### debug_callback ###

* Logs message and possibly quits

### validate_extesions ###

* Returns if list of desired extensions are present in properties list

### validate_layers ###

* Return if list of desired layers are present in properties list

### find_shader_stage ###

* Returns VkShaderStageFlagBits associated with filename extension

### init_instance ###

* initialise vulkan instance

### init_device ###

* enumerate devices
* find physical device which has a graphics queue which supports presentation
* create the device with one graphcs queue
* get the queue

### teardown_per_frame ###

This is done for each frame in the swap chain

* destroy submit fence
* free command buffers
* destroy command pool
* destroy acquire semaphore
* destroy release semaphore

### load_shader_module ###

* create instance of vkb glsl compiler
* load file
* compile shader, using correct shader stage
* create a shader module with the resulting spirv

### acquire_next_image ###

* Acquire a semaphore - either a new one or one from the recycle pile
* Wait for any fences for this acquired image - wait for previous frame to finish rendering. This should just return immediately as it's a old frame in the chain.
* Reset the command pool for the frame
* Recycle the old semaphore for the frame - back to the heap
* Store the new acquire semaphore as part of the frame data

### render_triangle ###

* get frame buffer to render in to
* grab the frames command buffer
* begin the command buffer
	* set clear value
	* begin render pass
	* bind the graphics pipeline
	* set the viewport
	* set the scissor
	* draw 3 vertices
	* end the render pass
* end the command buffer
* create a release semaphore
* submit the buffer to the queue with semaphore

### present_image ###

* present swapchain image with swapchain release semaphore

### teardown_framebuffers ###

* Wait for the queue to be idle
* Destroy all the Framebuffer objects
* Clear the context framebuffer vector

### teardown ###

* wait for device idle
* teardown_framebuffers()
* teardown_per_frame * n
* destroy recycled samephores
* destroy pipeline
* destroy pipeline layout
* destroy render pass
* destroy swap chain image views
* destroy swap chain
* destroy window surface
* destroy device
* destroy debug callback
* reset vkb::instance

### init_render_pass

* Create single attachment description - simple clear/store image present
* Create subpass - one color attachment, the one just created
* Create subpass dependency
* Create render pass - one attachment, one subpass, one dependency

### init_swapchain

* Get the surface capabilities for the window surface. Pixel format, swapchain image counts, size etc...
* Get the physical device surface formats whixh are supported for the window surface
* Work out the best format and create the swapchain with it
* If there was an old swapchain, destroy it... first iterate over the swapchain image views and destroy them, then destroy the old swapchain object itself
* Now grab the new swapchain images and initialise their resources one by one. 
* Iterate over the swapchain images and create image views for each one.

### init_per_frame

This is done for each image in the swapchain

* Create a VkFence for queue submit. The CPU will wait for this when acquiring next image to render in to.
* Create a command pool to hold the commandbuffers to render in to the image
* Allocate a primary command buffer from the pool

### init_pipeline

* Create pipeline layout
* Create all the state create info structures
	* Vertex input
	* Input assembly
	* Rasterization
	* Color blend
	* Viewport
	* Depth stencil
	* Multisample
	* Dynamic
* Create vertex shader and add to shader stages array
* Create fragment shader and add to shader stages array
* Create the pipeline...
* Destroy shader modules

### init_framebuffers

* Iterate over the swapchain image views
	* Create framebuffer object from the image view