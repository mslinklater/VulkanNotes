# Sample Details

|Sample|CPP|vkb App|ApiVulkanSample|
|---|---|---|---|
|compute-nbody|NO|NO|YES|
|hello-triangle|NO|YES|NO|
|hpp-hello-triangle|YES|YES|NO|

# Class Hierarchy

* vkb::Application
	* HelloTriangle
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
			* HPPPipelineCache
			* HPPSwapchainImages
		* HPPHelloTriangle
	* vkb::VulkanSample
		* AFBCSample
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
			* MultiDrawIndirect (perf)
			* OpenCLInterop (ext)
			* OpenGLInterop (ext)
			* Portability (ext)
			* Profiles (tooling)
			* PushDescriptors (ext)
			* RayQueries (ext)
			* RaytracingReflection (ext)
			* RaytracingBasic (ext)
			* RaytracingExtended (ext)
			* SeparateImageSampler (api)
			* Synchronization2 (ext)
			* TerrainTessellation (api)
			* TextureCompressionBasisu (perf)
			* TextureLoading (api)
			* TextureMipMapGeneration (api)
			* TimelineSemaphore (ext)
			* TimestampQueries (api)
			* VertexDynamicState (ext)
		* AsyncComputeSample
		* CommandBufferUsage
		* ConstantData
		* DescriptorManagement
		* KHR16BitArithmeticSample
		* KHR16BitStorageInputOutputSample
		* LayoutTrasitions
		* MSAASample
		* MultithreadingRenderPasses
		* PipelineBarriers
		* PipelineCache
		* RenderPassesSample
		* SpecializationConstants
		* Subpasses
		* SurfaceRotation
		* SwapchainImages
		* TextureCompressionComparison
		* WaitIdle
* vkb::BufferAllocation
* vkb::BufferBlock
* vkb::BufferPool
* vkb::Camera
* vkb::DebugInfo
* vkb::Device
* vkb::Drawer
* vkb::FencePool
* vkb::field::Base
	* vkb::field::Dynamic
		* vkb::field::MinMax
	* vkb::field::Static
		* vkb::field::Vector
* vkb::GLSLCompiler
* vkb::GLTFLoader
* vkb::Window
