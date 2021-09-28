# Microsoft Edge TTS for Home Assistant

This component is based on the TTS service of Microsoft Edge browser, no need to apply for `app_key`.


## Install

> Download and copy `custom_components/edge_tts` folder to `custom_components` folder in your HomeAssistant config folder

```shell
# Auto install via terminal shell
wget -q -O - https://cdn.jsdelivr.net/gh/al-one/hass-xiaomi-miot/install.sh | DOMAIN=edge_tts REPO_PATH=hasscc/hass-edge-tts bash -
```


## Config

```yaml
# configuration.yaml
tts:
  - platform: edge_tts
    language: zh-CN # Default language or voice (Optional)
```

### Supported languages

- [adjust-speaking-languages](https://docs.microsoft.com/zh-CN/azure/cognitive-services/speech-service/speech-synthesis-markup?tabs=csharp#adjust-speaking-languages)
- [list of voices](https://speech.platform.bing.com/consumer/speech/synthesize/readaloud/voices/list?trustedclienttoken=6A5AA1D4EAFF4E9FB37E23D68491D6F4)


## Using

[![Call service: tts.edge_tts_say](https://my.home-assistant.io/badges/developer_call_service.svg)](https://my.home-assistant.io/redirect/developer_call_service/?service=tts.edge_tts_say)

### Options

- [`voice`](https://docs.microsoft.com/zh-CN/azure/cognitive-services/speech-service/speech-synthesis-markup?tabs=csharp#use-multiple-voices)
- [`style`](https://docs.microsoft.com/zh-CN/azure/cognitive-services/speech-service/speech-synthesis-markup?tabs=csharp#adjust-speaking-styles)
- `styledegree`: 0.01 - 2, only for `zh-CN`
- `role`: only for `zh-CN-XiaomoNeural` `zh-CN-XiaoxuanNeura`
  - Girl
  - Boy
  - YoungAdultFemale
  - YoungAdultMale
  - OlderAdultFemale
  - OlderAdultMale
  - SeniorFemale
  - SeniorMale
- [`pitch` / `rate` / `volume`](https://docs.microsoft.com/zh-CN/azure/cognitive-services/speech-service/speech-synthesis-markup?tabs=csharp#adjust-prosody)

### Basic example

```yaml
service: tts.edge_tts_say
data:
  entity_id: media_player.your_player_entity_id
  message: Hello
  language: zh-CN-XiaoxiaoNeural # Language or voice (Optional)

```

### Full example

```yaml
service: tts.edge_tts_say
data:
  entity_id: media_player.your_player_entity_id
  message: 吃葡萄不吐葡萄皮，不吃葡萄倒吐葡萄皮
  language: zh-CN
  cache: true
  options:
    voice: zh-CN-XiaomoNeural
    style: cheerful
    styledegree: 2
    role: Girl
    pitch: +0Hz
    rate: +0%
    volume: +10%
```


## Thanks

- https://github.com/rany2/edge-tts
- https://github.com/ag2s20150909/TTS