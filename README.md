# Surge-Adblock




[Rule]
RULE-SET,https://raw.githubusercontent.com/app2smile/rules/master/rule/tieba-ad.list,REJECT-DROP

[MITM]
hostname = %APPEND% tiebac.baidu.com

[Script]
贴吧json = type=http-response,pattern=^http(s:\/\/tiebac|:\/\/c\.tieba)\.baidu\.com\/(c\/(s\/sync|f\/(frs\/(page|threadlist|generalTabList)|pb\/(pic)?page|excellent\/personalized))$|tiebaads\/commonbatch\?),requires-body=1,max-size=0,script-path=https://raw.githubusercontent.com/app2smile/rules/master/js/tieba-json.js,script-update-interval=0
贴吧proto = type=http-response,pattern=^http(s:\/\/tiebac|:\/\/c\.tieba)\.baidu\.com\/c\/f\/(frs\/(page|threadlist|generalTabList)|pb\/page|excellent\/personalized)\?cmd,requires-body=1,binary-body-mode=1,max-size=-1,script-path=https://raw.githubusercontent.com/app2smile/rules/master/js/tieba-proto.js,argument=per_filter_video_thread={{{per_filter_video}}}
