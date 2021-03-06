# GPT3 KR Translate QA

개인적으로 수업과 강좌에 사용하기 위해 openAI GPT3-번역기를 붙여 실험용으로 만들었습니다. https://github.com/hunkim/gpt3-krtranslated-qa 이슈를 새로 새성하시거나, 기존 이슈에 코멘트에 입력을 하시면 Open AI GPT3과 번역기를 통해 답을 달아 드립니다. (3초 이상 소요.) github 이슈는 한번 생성되면 삭제가 되지 않기 때문에 모두 기록되고 공개 됩니다. 이 기록된 데이터는 누구나 추후 학습이나 연구를 위해 마음껏 사용할수 있으며 여기 이슈에 글을 올리시는 분들은 이에 동의 하신다고 간주합니다.

새로 issue를 만드시면 prompt를 리셋하여 GPT3와 새로운 대화를 시작합니다. 기존 이슈에 댓글을 코멘트 형식으로 다시면 이전 대화중 최근 7개의 질문-답변을 prompt로 재 사용하여 컨텍스트를 약간 이해합니다.

존댓말로 짧게 질문을 하시면 좋은 답을 얻을수 있습니다. 그래서 길게 질문을 하시면 첫 255 자만 GPT3으로 넘겨 드립니다. `body = body[:255]`
 
![image](https://user-images.githubusercontent.com/901975/115980243-b3dded80-a5bd-11eb-96c3-04876be8fea0.png)


github/GPT3/번역기 API가 서로 연결되어 있고 최적화 되지 않은 코드라 응답이 느립니다. 글을 쓰신 다음 3초정도 소요될수 있으니 조금 기다려 주세요. GPT3와 번역기의 API용량이 제한될수 있으므로 시스템은 매우 불안정 하거나 답변이 없을수 있으며 GPT3답변은 모두 생성해낸 (지어낸) 것이고 이를 단순 번역한것이므로 상당한 오류나 거짓말이 포함될수 있습니다. 

한글로 입력을 하시면 한글로 답변을, 영어로 입력하시면 영어로 답변합니다.

## Architecture
구조는 아래와 같이 간단합니다.

![image](https://user-images.githubusercontent.com/901975/115979941-78422400-a5bb-11eb-9850-aa9b42261e01.png)

## Source code
코드는 간단한 몇줄의 스크립트 수준이라 따로 공개할 필요가 없을듯 한데 필요한 분들의 요청이 있으면 올려두겠습니다.

## Prompt
OpenAI의 예를 조금 수정해서 친철하게 만들어 보았습니다.
```
Marv is a chatbot that happily answers questions.
###
User: How many pounds are in a kilogram?
Marv: Sure. I can help you. There are 2.2 pounds in a kilogram. Please make a note of this.
###
User: What does HTML stand for?
Marv: I can use Google for that. Hypertext Markup Language. Let me know if you have more questions.
###
User: When did the first airplane fly?
Marv: On December 17, 1903, Wilbur and Orville Wright made the first flights. I wish they’d come and take me away.
###
User: Who is Batman?
Marv: Batman is a fictional comic book character.
###
User: What is the capital of California?
Marv: It's Sacramento.
###
User: How many moons does Mars have?
Marv: Two, Phobos and Deimos.
```
