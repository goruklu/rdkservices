<!-- Generated automatically, DO NOT EDIT! -->
<a name="head.TextToSpeech_Plugin"></a>
# TextToSpeech Plugin

**Version: 1.0**

**Status: :black_circle::black_circle::black_circle:**

TextToSpeech plugin for Thunder framework.

### Table of Contents

- [Introduction](#head.Introduction)
- [Description](#head.Description)
- [Configuration](#head.Configuration)
- [Methods](#head.Methods)
- [Notifications](#head.Notifications)

<a name="head.Introduction"></a>
# Introduction

<a name="head.Scope"></a>
## Scope

This document describes purpose and functionality of the TextToSpeech plugin. It includes detailed specification of its configuration, methods provided and notifications sent.

<a name="head.Case_Sensitivity"></a>
## Case Sensitivity

All identifiers on the interface described in this document are case-sensitive. Thus, unless stated otherwise, all keywords, entities, properties, relations and actions should be treated as such.

<a name="head.Acronyms,_Abbreviations_and_Terms"></a>
## Acronyms, Abbreviations and Terms

The table below provides and overview of acronyms used in this document and their definitions.

| Acronym | Description |
| :-------- | :-------- |
| <a name="acronym.API">API</a> | Application Programming Interface |
| <a name="acronym.HTTP">HTTP</a> | Hypertext Transfer Protocol |
| <a name="acronym.JSON">JSON</a> | JavaScript Object Notation; a data interchange format |
| <a name="acronym.JSON-RPC">JSON-RPC</a> | A remote procedure call protocol encoded in JSON |

The table below provides and overview of terms and abbreviations used in this document and their definitions.

| Term | Description |
| :-------- | :-------- |
| <a name="term.callsign">callsign</a> | The name given to an instance of a plugin. One plugin can be instantiated multiple times, but each instance the instance name, callsign, must be unique. |

<a name="head.References"></a>
## References

| Ref ID | Description |
| :-------- | :-------- |
| <a name="ref.HTTP">[HTTP](http://www.w3.org/Protocols)</a> | HTTP specification |
| <a name="ref.JSON-RPC">[JSON-RPC](https://www.jsonrpc.org/specification)</a> | JSON-RPC 2.0 specification |
| <a name="ref.JSON">[JSON](http://www.json.org/)</a> | JSON specification |
| <a name="ref.Thunder">[Thunder](https://github.com/WebPlatformForEmbedded/Thunder/blob/master/doc/WPE%20-%20API%20-%20WPEFramework.docx)</a> | Thunder API Reference |

<a name="head.Description"></a>
# Description

The TextToSpeech plugin provides TTS functionality (Voice Guidance & Speech Synthesis) for the client application.

The plugin is designed to be loaded and executed within the Thunder framework. For more information about the framework refer to [[Thunder](#ref.Thunder)].

<a name="head.Configuration"></a>
# Configuration

The table below lists configuration options of the plugin.

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| callsign | string | Plugin instance name (default: *org.rdk.TextToSpeech*) |
| classname | string | Class name: *TextToSpeech* |
| locator | string | Library name: *libWPEFrameworkTextToSpeech.so* |
| autostart | boolean | Determines if the plugin is to be started automatically along with the framework |

<a name="head.Methods"></a>
# Methods

The following methods are provided by the TextToSpeech plugin:

TextToSpeech interface methods:

| Method | Description |
| :-------- | :-------- |
| [isttsenabled](#method.isttsenabled) | Check whether TTS Engine is enabled or not |
| [speak](#method.speak) | Start Speech |
| [cancel](#method.cancel) | cancel the speech |

<a name="method.isttsenabled"></a>
## *isttsenabled <sup>method</sup>*

Check whether TTS Engine is enabled or not.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |

### Result

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| result | object |  |
| result?.isenabled | boolean | <sup>*(optional)*</sup> Indicates whether TTSEngine is enabled or not |
| result?.TTS_Status | number | <sup>*(optional)*</sup> TTS Return status (must be one of the following: *TTS_OK*, *TTS_FAIL*, *TTS_NOT_ENABLED*, *TTS_INVALID_CONFIGURATION*) |
| result?.success | boolean | <sup>*(optional)*</sup> Call status |

### Example

#### Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "TextToSpeech.1.isttsenabled",
    "params": {}
}
```
#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": {
        "isenabled": true,
        "TTS_Status": 0,
        "success": true
    }
}
```
<a name="method.speak"></a>
## *speak <sup>method</sup>*

Start Speech.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.text | string | Text input |

### Result

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| result | object |  |
| result?.speechid | number | <sup>*(optional)*</sup> Indicates the speechid created by TTSEngine |
| result?.TTS_Status | number | <sup>*(optional)*</sup> TTS Return status (must be one of the following: *TTS_OK*, *TTS_FAIL*, *TTS_NOT_ENABLED*, *TTS_INVALID_CONFIGURATION*) |
| result?.success | boolean | <sup>*(optional)*</sup> Call status |

### Example

#### Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "TextToSpeech.1.speak",
    "params": {
        "text": "speech_1"
    }
}
```
#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": {
        "speechid": 1,
        "TTS_Status": 0,
        "success": true
    }
}
```
<a name="method.cancel"></a>
## *cancel <sup>method</sup>*

cancel the speech.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.speechid | number | Specify speechid to cancel the speech |

### Result

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| result | object |  |
| result?.TTS_Status | number | <sup>*(optional)*</sup> TTS Return status (must be one of the following: *TTS_OK*, *TTS_FAIL*, *TTS_NOT_ENABLED*, *TTS_INVALID_CONFIGURATION*) |
| result?.success | boolean | <sup>*(optional)*</sup> Call status |

### Example

#### Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "TextToSpeech.1.cancel",
    "params": {
        "speechid": 1
    }
}
```
#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": {
        "TTS_Status": 0,
        "success": true
    }
}
```
<a name="head.Notifications"></a>
# Notifications

Notifications are autonomous events, triggered by the internals of the implementation, and broadcasted via JSON-RPC to all registered observers.Refer to [[Thunder](#ref.Thunder)] for information on how to register for a notification.

The following events are provided by the TextToSpeech plugin:

TextToSpeech interface events:

| Event | Description |
| :-------- | :-------- |
| [onspeechstart](#event.onspeechstart) | Notifies when speech starts |
| [onspeechinterrupted](#event.onspeechinterrupted) | Notifies when the current speech is cancelled |
| [onnetworkerror](#event.onnetworkerror) | Notifies when network error is occurred |
| [onplaybackerror](#event.onplaybackerror) | Notifies when playback error |
| [onspeechcomplete](#event.onspeechcomplete) | Notifies when speech is completed |

<a name="event.onspeechstart"></a>
## *onspeechstart <sup>event</sup>*

Notifies when speech starts.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.speechid | number | Speech Id |
| params.text | string | Text |

### Example

```json
{
    "jsonrpc": "2.0",
    "method": "client.events.1.onspeechstart",
    "params": {
        "speechid": 1,
        "text": "speech_1"
    }
}
```
<a name="event.onspeechinterrupted"></a>
## *onspeechinterrupted <sup>event</sup>*

Notifies when the current speech is cancelled.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.speechid | number | Speech Id |

### Example

```json
{
    "jsonrpc": "2.0",
    "method": "client.events.1.onspeechinterrupted",
    "params": {
        "speechid": 1
    }
}
```
<a name="event.onnetworkerror"></a>
## *onnetworkerror <sup>event</sup>*

Notifies when network error is occurred.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.speechid | number | Speech Id |

### Example

```json
{
    "jsonrpc": "2.0",
    "method": "client.events.1.onnetworkerror",
    "params": {
        "speechid": 1
    }
}
```
<a name="event.onplaybackerror"></a>
## *onplaybackerror <sup>event</sup>*

Notifies when playback error.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.speechid | number | Speech Id |

### Example

```json
{
    "jsonrpc": "2.0",
    "method": "client.events.1.onplaybackerror",
    "params": {
        "speechid": 1
    }
}
```
<a name="event.onspeechcomplete"></a>
## *onspeechcomplete <sup>event</sup>*

Notifies when speech is completed.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.speechid | number | Speech Id |
| params.text | string | Text |

### Example

```json
{
    "jsonrpc": "2.0",
    "method": "client.events.1.onspeechcomplete",
    "params": {
        "speechid": 1,
        "text": "speech_1"
    }
}
```
