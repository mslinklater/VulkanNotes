# Hello triangle

*source:* samples/api/hello_triangle/hello_triangle.cpp

---

## Pseudocode

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

## init_render_pass

Create since attachment description - imple clear/store image present
Create subpass - one color attachment, the one just created
Create subpass dependency
Create render pass - one attachment, one subpass, one dependency

## init_swapchain

* Get the surface capabilities for the window surface. Pixel format, swapchain image counts, size etc...
* Get the physical device surface formats whixh are supported for the window surface
* Work out the best format and create the swapchain with it
* If there was an old swapchain, destroy it... first iterate over the swapchain image views and destroy them, then destroy the old swapchain object itself
* Now grab the new swapchain images and initialise their resources one by one. 
* Iterate over the swapchain images and create image views for each one.

## init_per_frame

This is done for each image in the swapchain

* Create a VkFence for queue submit. The CPU will wait for this when acquiring next image to render in to.
* Create a command pool to hold the commandbuffers to render in to the image
* Allocate a primary command buffer from the pool