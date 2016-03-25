
### Deploy to hockeyapp

Spent a lot of time trying to figure out the right command to use, let's
save it here once and for all :

```shell
curl -v \
  -F "status=2" \
  -F "notify=1" \
  -F "ipa=@build/outputs/apk/app.apk" \
  -H "X-HockeyAppToken: my-hockeyapp-token" \
  https://rink.hockeyapp.net/api/2/apps/app_id/app_versions/upload
```
