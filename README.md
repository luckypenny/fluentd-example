# Step 1 : Install td-agent
- https://docs.fluentd.org/installation/install-by-dmg
- brew install td-agent

# Step 2 : Launch td-agent
cat /Library/LaunchDaemons/td-agent.plist
sudo launchctl load /Library/LaunchDaemons/td-agent.plist
less /var/log/td-agent/td-agent.log

cat /etc/td-agent/td-agent.conf
sudo launchctl unload /Library/LaunchDaemons/td-agent.plist

- 로그가 쓰이지 않아 포어 그라운드로 실행 
- https://jangseongwoo.github.io/fluentd/fluentd_install/
- sudo /opt/td-agent/usr/sbin/td-agent -c /etc/td-agent/td-agent.conf

# Step 3 : Post Sample Logs via HTTP
https://ksr930.tistory.com/141
https://minimilab.tistory.com/61

sudo /opt/td-agent/usr/sbin/td-agent -c `pwd`/in_http.conf

curl -i -X POST -d 'json={"action":"login","user":2}' http://localhost:8888/test.cycle
