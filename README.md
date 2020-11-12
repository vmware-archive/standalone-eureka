# standalone-eureka is no longer actively maintained by VMware.

# standalone-eureka
Standalone eureka instance for use on PWS, for experimental and demo purposes.

It's pretty straightforward to get this thing running:
```bash
$ git clone https://github.com/cf-platform-eng/standalone-eureka.git
$ cd standalone-eureka
```

Then, edit the manifest.yml file to give the project some sort of unique name:
```
---
applications:
- name: some-sort-of-unique-name
  memory: 512M
  instances: 1
  host: standalone-eureka
  path: target/standalone-eureka-1.0.0.jar
  env:
    SPRING_PROFILES_ACTIVE: cloud
```
Then, build and push to CF:

```bash
$ mvn clean install
$ cf push
```
Finally, take a look at the console to see what eureka is up to. 

In the example above the console would be accessible via: http://some-sort-of-unique-name.cfapps.io/
