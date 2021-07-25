

* 설치 후 channel 에 메시지 전송할 app 만들기
    * app 만들기 : https://api.slack.com/apps/A0293G83VM1
    * Incoming webhooks 
        * 설정 : https://api.slack.com/apps/A0293G83VM1/incoming-webhooks?
        * project-demo : https://hooks.slack.com/services/T029FV6J5U1/B0293GKK3GT/ bECRxTtbHQ0d0ndEqiFgar0y
        * 일반 : https://hooks.slack.com/services/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
        * curl -X POST --data-urlencode "payload={'text': 'This is posted to #general and comes from a bot named webhookbot.'}"  https://hooks.slack.com/services/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

    * json format : https://app.slack.com/block-kit-builder


* 참고
    * https://helloworld.kurly.com/blog/slack_block_kit/
    * https://surpassing.tistory.com/713
