Python SDK For Vdisk
=====

<h3>Vdisk Documentation</h3>

http://vdisk.weibo.com/developers/index.php?module=api&action=apidoc

<h3>Usage</h3>
Get the authorization url.
###

    from vdisk import OAuth2
    oauth = OAuth2(WEIPAN_APPKEY,WEIPAN_APPSECRET,WEIPAN_CALLBACK)
    url = oauth.authorize()
###
In the callback url.
###

    oauth = OAuth2(WEIPAN_APPKEY,WEIPAN_APPSECRET,WEIPAN_CALLBACK)
    #use web.py framework
    i = web.input()
    if i.code.isdigit() and int(i.code) == 21330:
        return i.msg
    try:
        return oauth.access_token(code = i.code)
###
Request for data using access_token.
###

    obj = Client()
    return obj.account_info(access_token)
###
<h3>Example</h3>
1. Get access_token
   request for this url: http://pzhu001.sinaapp.sina.com/auth
   after authorization you will get access_token
2. <h4/>Then request for vdisk api using access_token<h4/>
   <h4>account/info</h4>
   http://pzhu001.sinaapp.com/2/account/info?access_token=f9c6606661ckiME21a9PM3CSQkI60b0a
   <h4>metadata</h4>
   In this example,parameter path has to be passed by GET method. root is set to basic.<br/>
   http://pzhu001.sinaapp.com/2/metadata?access_token=f9c6606661ckiME21a9PM3CSQkI60b0a&path=/

