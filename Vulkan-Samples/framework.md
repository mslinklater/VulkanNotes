# Framework

Details of the platform-agnostic framework code that all the Vulkan-Samples use.

## Execution

* main
* platform.initialize
	* create_window
* platform.main_loop
	* if app_requested
		* start_app
			* **active_app->constructor**
			* **active_app->prepare**
		* **active_app->update**
	* update
		* **active_app->update**
	* window process events
* platform.terminate
	* **active_app->destructor**
* exit