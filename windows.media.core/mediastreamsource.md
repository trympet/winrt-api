---
-api-id: T:Windows.Media.Core.MediaStreamSource
-api-type: winrt class
---

<!-- Class syntax.
public class MediaStreamSource : Windows.Media.Core.IMediaSource, Windows.Media.Core.IMediaStreamSource, Windows.Media.Core.IMediaStreamSource2, Windows.Media.Core.IMediaStreamSource3
-->

# Windows.Media.Core.MediaStreamSource

## -description
Represents a media source that delivers media samples directly to the media pipeline.

## -remarks
See the [MediaStreamSource Sample](https://github.com/microsoftarchive/msdn-code-gallery-microsoft/tree/master/Official%20Windows%20Platform%20Sample/MediaStreamSource%20streaming%20sample) for an example of using Media Stream Source in a UWP app.

MediaStreamSource is a new generic media source for UWP apps which is introduced in Windows 8.1. MediaStreamSource allows apps to send compressed or uncompressed audio and video samples to the media pipeline for playback, transcoding, and streaming. Media samples can be dynamically generated by the app, or de-multiplexed from a stream or files. This flexibility enables apps to more easily extend platform support for new media formats or solve complex problems, such as adaptive streaming.

The MediaStreamSourceAPI are very similar to the Microsoft SilverlightAPI of the same name.

MediaStreamSource can be used with [audio](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/audio) and [video](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video) objects in Windows app using JavaScript, [MediaElement](../windows.ui.xaml.controls/mediaelement.md) objects in UWP apps using C++, C#, or Visual Basic, and the [MediaTranscoder](../windows.media.transcoding/mediatranscoder.md).

 The [MediaStreamSource Sample](https://github.com/microsoftarchive/msdn-code-gallery-microsoft/tree/master/Official%20Windows%20Platform%20Sample/MediaStreamSource%20streaming%20sample) demonstrates how to use the MediaStreamSource. Here are some of the main MediaStreamSource API. The order outlines the basic flow of how MediaStreamSource functions. You'll notice that the MediaStreamSource sends request objects to the app through event arguments. These request objects enable the app to interact with the MediaStreamSource and pass data back to it.


| API                   | Description                                   |
|-----------------------|-----------------------------------------------|
| **MediaStreamSource** | Represents a media source that delivers media samples directly to the media pipeline. MediaStreamSource consumes [MediaStreamSample](mediastreamsample.md) objects that are provided by the application. |
| [MediaStreamSample](mediastreamsample.md) | Represents a media sample used by the MediaStreamSource. |
| [MediaStreamSource.Starting](mediastreamsource_starting.md) (event) | The MediaStreamSource uses this event to notify the app that it is ready to start processing media data. |
| [MediaStreamSourceStartingRequest](mediastreamsourcestartingrequest.md) | Represents a request from the MediaStreamSource that it is ready to start processing media data. Apps should reply as soon as possible to this request by calling [SetActualStartPosition](mediastreamsourcestartingrequest_setactualstartposition_661405035.md) on the request. If an app needs to delay the MediaStreamSource from processing data, it can get an asynchronous deferral from [MediaStreamSourceStartingRequest.GetDeferral](mediastreamsourcestartingrequest_getdeferral_254836512.md). When the app is ready for the MediaStreamSource to start, it calls [Complete](mediastreamsourcestartingrequestdeferral_complete_1807836922.md) on the deferral object. The starting request is accessed through the [MediaStreamSourceStartingEventArgs](mediastreamsourcestartingeventargs.md) that are passed to the [MediaStreamSource.Starting](mediastreamsource_starting.md) event handler.|
| [MediaStreamSource.SampleRequested](mediastreamsource_samplerequested.md) (event) | The MediaStreamSource uses this event to notify the app that it is ready for a [MediaStreamSample](mediastreamsample.md). Apps are required to register a handler for this event. |
| [MediaStreamSourceSampleRequest](mediastreamsourcesamplerequest.md) | Represents a request from the MediaStreamSource for a new media sample. Setting the [Sample](mediastreamsourcesamplerequest_sample.md) property to the new [MediaStreamSample](mediastreamsample.md) triggers the MediaStreamSource to retrieve the media sample and continue processing the media data. Apps should reply as soon as possible to this request. If an app needs time before sending the [MediaStreamSample](mediastreamsample.md), it can get an asynchronous deferral from [MediaStreamSourceSampleRequest.GetDeferral](mediastreamsourcesamplerequest_getdeferral_254836512.md). When the app is finished with the deferral, it calls [Complete](mediastreamsourcesamplerequestdeferral_complete_1807836922.md) on the deferral object. The sample request is accessed through the [MediaStreamSourceSampleRequestedEventArgs](mediastreamsourcesamplerequestedeventargs.md) that are passed to the [MediaStreamSource.SampleRequest](mediastreamsource_samplerequested.md) event handler. The app indicates it has reached the end of the stream by responding to a [MediaStreamSourceSampleRequest](mediastreamsourcesamplerequest.md) without providing a [MediaStreamSample](mediastreamsample.md), or by assigning the [MediaStreamSourceSampleRequest.Sample](mediastreamsourcesamplerequest_sample.md) property to **null**. |
| [MediaStreamSource.Closed](mediastreamsource_closed.md) (event) | The MediaStreamSource uses this event to notify the app that it has shut down. |
| [MediaStreamSourceClosedRequest](mediastreamsourceclosedrequest.md) | Represents a request from the MediaStreamSource that it has closed. The close request is accessed through the [MediaStreamSourceClosedEventArgs](mediastreamsourceclosedeventargs.md) that are passed to the [MediaStreamSource.Closed](mediastreamsource_closed.md) event handler. |
| [MediaElement.SetMediaStreamSource](../windows.ui.xaml.controls/mediaelement_setmediastreamsource_1064978867.md) | Sets the source of the [MediaElement](../windows.ui.xaml.controls/mediaelement.md) to a MediaStreamSource. |

### Version history

| Windows version | SDK version | Value added |
| -- | -- | -- |
| 1607 | 14393 | SampleRendered |
| 1703 | 15063 | MaxSupportedPlaybackRate |
| 1709 | 16299 | IsLive |

## -examples

## -see-also
[IMediaSource](imediasource.md), [MediaStreamSource Sample](https://github.com/microsoftarchive/msdn-code-gallery-microsoft/tree/master/Official%20Windows%20Platform%20Sample/MediaStreamSource%20streaming%20sample)
