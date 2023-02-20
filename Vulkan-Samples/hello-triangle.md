# Hello triangle

*source:* samples/api/hello_triangle/hello_triangle.cpp

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