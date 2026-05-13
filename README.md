Express
=======

#### Install
```bash
npm init -y
npm install express --save
node app.js
```

Openshift
=======
```bash 
oc new-app --name=express https://github.com/moukail/express-react-demo.git

oc delete service express
oc expose deployment/express --name=express --port=80 --target-port=3000
oc create route edge express --service=express --insecure-policy=Redirect

curl https://express-express-demo.apps-crc.testing -k

oc delete deployment,svc,bc,is,route express

### s2i
chmod +x .s2i/bin/assemble
chmod +x .s2i/bin/run

oc import-image nodejs:18 --from=registry.access.redhat.com/ubi8/nodejs-18 --confirm -n openshift
oc new-app nodejs:18~https://github.com/moukail/express-react-demo.git --name=express

```
