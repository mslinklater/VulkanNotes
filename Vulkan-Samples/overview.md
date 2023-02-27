# Sample Details

|Sample|CPP|vkb App|ApiVulkanSample|
|---|---|---|---|
|compute-nbody|NO|NO|YES|
|hello-triangle|NO|YES|NO|
|hpp-hello-triangle|YES|YES|NO|

# Class Hierarchy

* vkb::Application
	* vkb::VulkanSample
		* ApiVulkanSample
			* BufferDeviceAddress (ext)
			* ComputeNBody (api)
			* ConditionalRendering (ext)
			* ConservativeRasterization (ext)
			* DebugUtils (ext)
			* DescriptorIndexing (ext)
			* DynamicRendering (ext)
			* DynamicUniformBuffers (api)
			* FragmentShadingRate (ext)
			* FragmentShadingRateDynamic (ext)
			* GraphicsPipelineLibrary (ext)
			* HDR (api)
			* HlslShaders (api)
			* Instancing (api)
			* OpenCLInterop (ext)
			* OpenGLInterop (ext)
			* Portability (ext)
			* PushDescriptors (ext)
			* RayQueries (ext)
			* RaytracingReflection (ext)
			* RaytracingBasic (ext)
			* RaytracingExtended (ext)
			* SeparateImageSampler (api)
			* Synchronization2 (ext)
			* TerrainTessellation (api)
			* TextureLoading (api)
			* TextureMipMapGeneration (api)
			* TimelineSemaphore (ext)
			* TimestampQueries (api)
			* VertexDynamicState (ext)
		* KHR16BitArithmeticSample
		* KHR16BitStorageInputOutputSample
		* AFBCSample
		* AsyncComputeSample
		* CommandBufferUsage
		* ConstantData
	* vkb::platform::HPPApplication
		* vkb::HPPVulkanSample
			* HPPApiVulkanSample
				* HPPComputeNBody (api)
				* HPPDynamicUniformBuffers (api)
				* HPPHDR (api)
				* HPPHlslShaders (api)
				* HPPInstancing (api)
				* HPPSeparateImageSampler (api)
				* HPPTerrainTessellation (api)
				* HPPTextureLoading (api)
				* HPPTextureMipMapGeneration (api)
		* HPPHelloTriangle
	* HelloTriangle
