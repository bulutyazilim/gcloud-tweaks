# Only Allow Your IP to SSH

First create a rule with your name
```
gcloud compute --project "project-name" firewall-rules create "USER_NAME" --allow tcp:22-6000 --network "default" --source-ranges "127.0.0.2"
```

each time update it with current ip adress
```
gcloud compute --project "project-name" firewall-rules update "USER_NAME"  --source-ranges "$(wget http://ip.appspot.com -qO -)"
```

and after if you want to close the doors, change it with 127.0.0.2
```
gcloud compute --project "project-name" firewall-rules update "USER_NAME"  --source-ranges "127.0.0.2"
```
