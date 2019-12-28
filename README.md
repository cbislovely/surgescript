根据Onewayticket255大佬Surge-Script仓库修改

修改内容：脚本名称重命名。


```
[Rule]

RULE-SET,https://raw.githubusercontent.com/cbislovely/surgescript/master/ad.list,REJECT-TINYGIF



//ZhiHu
URL-REGEX,https://www.zhihu.com/api/v4/mcn/,REJECT-TINYGIF
URL-REGEX,https://api.zhihu.com/(ab|adx|fringe|drama|zst|commercial|ad-style-service|market/popover|search/(top|tab|preset)|.*(guide|recommendations|featured-comment-ad)),REJECT-TINYGIF
AND,((USER-AGENT,osee2*), (NOT,((DOMAIN-SUFFIX,zhihu.com))), (NOT,((DOMAIN-SUFFIX,zhimg.com)))),REJECT-TINYGIF

//BiliBili
URL-REGEX,https://app.bilibili.com/x/v2/(splash|search/(defaultword|square)),REJECT-TINYGIF
URL-REGEX,https://api.bilibili.com/x/v2/dm/advert,REJECT-TINYGIF
AND,((USER-AGENT,bili*), (NOT,((DOMAIN-SUFFIX,bilibili.com))),(NOT,((DOMAIN-SUFFIX,hdslb.com)))),REJECT-TINYGIF


[MITM]
hostname = api.zhihu.com, www.zhihu.com, app.bilibili.com, api.bilibili.com, api.live.bilibili.com


[Script]
http-response https://api.zhihu.com/moments\?(action|feed_type) requires-body=1,max-size=0,script-path=https://raw.githubusercontent.com/cbislovely/surgescript/master/surge_zhihu_feed.js,script-update-interval=-1
http-response https://api.zhihu.com/topstory/recommend requires-body=1,max-size=0,script-path=https://raw.githubusercontent.com/cbislovely/surgescript/master/surge_zhihu_recommend.js,script-update-interval=-1
http-response https://api.zhihu.com/v4/questions requires-body=1,max-size=0,script-path=https://raw.githubusercontent.com/cbislovely/surgescript/master/surge_zhihu_answer.js,script-update-interval=-1
http-response https://api.zhihu.com/people/ requires-body=1,max-size=0,script-path=https://raw.githubusercontent.com/cbislovely/surgescript/master/surge_zhihu_people.js,script-update-interval=-1


http-response https://app.bilibili.com/x/v2/space\?access_key requires-body=1,max-size=0,script-path=https://raw.githubusercontent.com/cbislovely/surgescript/master/surge_bilibili_space.js,script-update-interval=-1
http-response https://app.bilibili.com/x/resource/show/tab\?access_key requires-body=1,max-size=0,script-path=https://raw.githubusercontent.com/cbislovely/surgescript/master/surge_bilibili_tab.js,script-update-interval=-1
http-response https://app.bilibili.com/x/v2/feed/index\?access_key requires-body=1,max-size=0,script-path=https://raw.githubusercontent.com/cbislovely/surgescript/master/surge_bilibili_feed.js,script-update-interval=-1
http-response https://app.bilibili.com/x/v2/account/mine\?access_key requires-body=1,max-size=0,script-path=https://raw.githubusercontent.com/cbislovely/surgescript/master/surge_bilibili_account.js,script-update-interval=-1
http-response https://app.bilibili.com/x/v2/view\?access_key requires-body=1,max-size=0,script-path=https://raw.githubusercontent.com/cbislovely/surgescript/master/surge_bilibili_view_relate.js,script-update-interval=-1
http-response https://api.bilibili.com/x/v2/reply/main\?access_key requires-body=1,max-size=0,script-path=https://raw.githubusercontent.com/cbislovely/surgescript/master/surge_bilibili_reply.js,script-update-interval=-1
http-response https://api.live.bilibili.com/xlive/app-room/v1/index/getInfoByRoom\?access_key requires-body=1,max-size=0,script-path=https://raw.githubusercontent.com/cbislovely/surgescript/master/surge_bilibili_live.js,script-update-interval=-1


//bilibili解锁番剧地区限制,目前还在测试,可能部分番剧会出现问题。
http-response https://api.bilibili.com/pgc/view/app/season requires-body=1,max-size=0,script-path=https://raw.githubusercontent.com/cbislovely/surgescript/master/surge_bilibili_season.js
http-response https://api.bilibili.com/pgc/player/api/playurl requires-body=1,max-size=0,script-path=https://raw.githubusercontent.com/cbislovely/surgescript/master/surge_bilibili_playurl.js

