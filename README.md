# Surge-Adblock
#百度贴吧，起点中文，高德地图，



[Rule]
# 百度贴吧
RULE-SET,https://raw.githubusercontent.com/app2smile/rules/master/rule/tieba-ad.list,REJECT-DROP
# 高德地图
AND,((URL-REGEX,"^http:\/\/.+\/amdc\/mobileDispatch",extended-matching),(USER-AGENT,"AMapiPhone*")),REJECT
DOMAIN,amap-aos-info-nogw.amap.com,REJECT,extended-matching,pre-matching
DOMAIN,free-aos-cdn-image.amap.com,REJECT,extended-matching,pre-matching
DOMAIN-SUFFIX,v.smtcdns.com,REJECT,extended-matching,pre-matching


[Map Local]
# 高德地图
^https:\/\/m5\.amap\.com\/ws\/shield\/search\/new_hotword\? data-type=text data="{}" status-code=200
^https:\/\/m5\.amap\.com\/ws\/faas\/amap-navigation\/card-service-(?:car-end|route-plan) data-type=text data="{}" status-code=200
^https:\/\/m5\.amap\.com\/ws\/shield\/search_poi\/tips_adv\? data-type=text data="{}" status-code=200
^https:\/\/oss\.amap\.com\/ws\/banner\/lists\/\? data-type=text data="{}" status-code=200
^https:\/\/m5\.amap\.com\/ws\/aos\/main\/page\/product\/list\? data-type=text data="{}" status-code=200
^https:\/\/m5\.amap\.com\/ws\/faas\/amap-navigation\/(?:main-page-assets|main-page-location|ridewalk-end-fc) data-type=text data="{}" status-code=200
^https:\/\/m5\.amap\.com\/ws\/(?:mapapi\/hint_text\/offline_data|message\/notice\/list|shield\/search\/new_hotword) data-type=text data="{}" status-code=200
^https:\/\/m5\.amap\.com\/ws\/shield\/scene\/recommend\? data-type=text data="{}" status-code=200
^https:\/\/m5\.amap\.com\/ws\/valueadded\/weather\/v2\? data-type=text data="{}" status-code=200
^https:\/\/sns\.amap\.com\/ws\/msgbox\/pull_mp\? data-type=text data="{}" status-code=200
^https:\/\/m5-zb\.amap\.com\/ws\/boss\/(?:order\/car\/king_toolbox_car_bubble|tips\/onscene_visual_optimization) data-type=text data="{}" status-code=200






[Script]
# 百度贴吧
贴吧json = type=http-response,pattern=^http(s:\/\/tiebac|:\/\/c\.tieba)\.baidu\.com\/(c\/(s\/sync|f\/(frs\/(page|threadlist|generalTabList)|pb\/(pic)?page|excellent\/personalized))$|tiebaads\/commonbatch\?),requires-body=1,max-size=0,script-path=https://raw.githubusercontent.com/app2smile/rules/master/js/tieba-json.js,script-update-interval=0
贴吧proto = type=http-response,pattern=^http(s:\/\/tiebac|:\/\/c\.tieba)\.baidu\.com\/c\/f\/(frs\/(page|threadlist|generalTabList)|pb\/page|excellent\/personalized)\?cmd,requires-body=1,binary-body-mode=1,max-size=-1,script-path=https://raw.githubusercontent.com/app2smile/rules/master/js/tieba-proto.js,argument=per_filter_video_thread={{{per_filter_video}}}
# 起点中文
起点json = type=http-response,pattern=^https:\/\/magev6\.if\.qidian\.com\/argus\/api\/(v4\/client\/getsplashscreen|v2\/(deeplink\/geturl|dailyrecommend\/getdailyrecommend)|v1\/(client\/getconf$|bookshelf\/getHoverAdv|adv\/getadvlistbatch\?positions=iOS_tab)),requires-body=1,max-size=0,script-path=https://raw.githubusercontent.com/app2smile/rules/master/js/qidian.js
body_rewrite_19 = type=http-response, pattern=^https:\/\/m5\.amap\.com\/ws\/shield\/search_business\/process\/marketingOperationStructured\?, script-path=https://raw.githubusercontent.com/Script-Hub-Org/Script-Hub/main/scripts/body-rewrite.js, requires-body=true, max-size=-1, timeout=30, argument=%5B%5B%22json-del%22%2C%5B%22data.commonMaterial%22%2C%22data.tipsOperationLocation%22%2C%22data.resourcePlacement%22%5D%5D%5D
# 高德地图
body_rewrite_20 = type=http-response, pattern=^https:\/\/m5\.amap\.com\/ws\/shield\/search_poi\/homepage\?, script-path=https://raw.githubusercontent.com/Script-Hub-Org/Script-Hub/main/scripts/body-rewrite.js, requires-body=true, max-size=-1, timeout=30, argument=%5B%5B%22json-del%22%2C%5B%22history_tags%22%5D%5D%5D
body_rewrite_30 = type=http-response, pattern=^https:\/\/m5-zb\.amap\.com\/ws\/sharedtrip\/taxi\/order_detail_car_tips\?, script-path=https://raw.githubusercontent.com/Script-Hub-Org/Script-Hub/main/scripts/body-rewrite.js, requires-body=true, max-size=-1, timeout=30, argument=%5B%5B%22json-del%22%2C%5B%22data.carTips.data.popupInfo%22%5D%5D%5D
移除路线规划推广 = type=http-response, pattern=^https:\/\/m5\.amap\.com\/ws\/aos\/perception\/publicTravel\/beforeNavi\?, script-path=https://kelee.one/Resource/Script/Amap/Amap_remove_ads.js, requires-body=true
移除路线规划、导航结束页推广 = type=http-response, pattern=^https:\/\/m5\.amap\.com\/ws\/bus\/plan\/integrate\?, script-path=https://kelee.one/Resource/Script/Amap/Amap_remove_ads.js, requires-body=true
移除导航详情页底部酒店 = type=http-response, pattern=^https:\/\/m5\.amap\.com\/ws\/c3frontend\/af-(?:hotel|launch)\/page\/main\?, script-path=https://kelee.one/Resource/Script/Amap/Amap_remove_ads.js, requires-body=true
移除路线规划推广 = type=http-response, pattern=^https:\/\/m5\.amap\.com\/ws\/perception\/drive\/(?:routeInfo|routePlan), script-path=https://kelee.one/Resource/Script/Amap/Amap_remove_ads.js, requires-body=true
移除导航详情页推广 = type=http-response, pattern=^https:\/\/m5\.amap\.com\/ws\/shield\/search\/(?:common\/coupon\/info|poi\/detail), script-path=https://kelee.one/Resource/Script/Amap/Amap_remove_ads.js, requires-body=true
移除搜索栏推广 = type=http-response, pattern=^https:\/\/m5\.amap\.com\/ws\/shield\/search_bff\/hotword\?, script-path=https://kelee.one/Resource/Script/Amap/Amap_remove_ads.js, requires-body=true
移除搜索详情页推广 = type=http-response, pattern=^https:\/\/m5\.amap\.com\/ws\/shield\/search_poi\/(?:mps|search\/sp|sug|tips_operation_location), script-path=https://kelee.one/Resource/Script/Amap/Amap_remove_ads.js, requires-body=true
移除首页推广 = type=http-response, pattern=^https:\/\/m5\.amap\.com\/ws\/faas\/amap-navigation\/(?:card-service-plan-home|main-page), script-path=https://kelee.one/Resource/Script/Amap/Amap_remove_ads.js, requires-body=true
移除首页推广 = type=http-response, pattern=^https:\/\/m5\.amap\.com\/ws\/shield\/frogserver\/aocs\/updatable\/1\?, script-path=https://kelee.one/Resource/Script/Amap/Amap_remove_ads.js, requires-body=true
移除我的页面推广 = type=http-response, pattern=^https:\/\/m5\.amap\.com\/ws\/shield\/dsp\/profile\/index\/nodefaasv3\?, script-path=https://kelee.one/Resource/Script/Amap/Amap_remove_ads.js, requires-body=true
移除附近页推广 = type=http-response, pattern=^https:\/\/m5\.amap\.com\/ws\/shield\/search\/nearbyrec_smart\?, script-path=https://kelee.one/Resource/Script/Amap/Amap_remove_ads.js, requires-body=true
移除开屏广告 = type=http-response, pattern=^https:\/\/m5\.amap\.com\/ws\/valueadded\/alimama\/splash_screen\?, script-path=https://kelee.one/Resource/Script/Amap/Amap_remove_ads.js, requires-body=true
移除打车页推广卡片、弹窗 = type=http-response, pattern=^https:\/\/m5-zb\.amap\.com\/ws\/boss\/(?:car\/order\/content_info|order_web\/friendly_information), script-path=https://kelee.one/Resource/Script/Amap/Amap_remove_ads.js, requires-body=true
移除打车页红点角标、天气图标 = type=http-response, pattern=^https:\/\/m5-zb\.amap\.com\/ws\/promotion-web\/resource(\/home)?\?, script-path=https://kelee.one/Resource/Script/Amap/Amap_remove_ads.js, requires-body=true


[MITM]
hostname = %APPEND% tiebac.baidu.com,magev6.if.qidian.com,m5.amap.com, m5-zb.amap.com, oss.amap.com, sns.amap.com,






