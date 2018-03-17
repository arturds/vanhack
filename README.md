# vanhack Devops Chalenge
The main idea is build a CI/CI pipelines like the image

![picture](https://github.com/arturds/vanhack/blob/master/diagram.png?raw=true)

# CI pipeline!

For this chalenge I install a Jenkins and create a folow mockup pipeline
![picture](https://github.com/arturds/vanhack/blob/master/cipipeline.png?raw=true)

- Instance Agent (not Implemented)
create a new instance and run a docker jenkins slave where job will run, con be used terraform or jenkins plugin, and can be deployable on aws, openstack etc

- Clone Repo
this step will clone the project repository

the next tree steps runs in parallel
- Unit testes
run project's unit testes
- Checkstyle
run checkstyle
- Code coverage
verify code coverage, can be used a bunch of plugins and methodos to do that, most important is well defined rules of coverage

- Integration Tests
run the system docker container and execute the suite of automatizad tests, and can be used for example selenium for interface, DB in memory etc.

- Stress Test
stresse system to enshure the performance, cam be used jmeter or gatling .

- Upload images
when all the steps finished with succees promove and upload the system image and start de CD pipeline


# CD pipeline
here are the cd pipeline proposal for a blue green deploy

![picture](https://github.com/arturds/vanhack/blob/master/cdpipeline.png?raw=true)

- Provide instances
create the instances where system will run (terraform)
- install system
run system containers
- production tests
test the instaled system, helt check, smoke test, etc. To assure the instalation and that system work properly
- change dns
change DNS to allow users to new version
- destroy old instances
destroy all old instances of the system

If the instance still working can check on this [Jenkins](http://54.159.171.176:8080/blue/pipelines/)
user: admin
password: admin

this pipeline not cover scaling the system, but it can be make with rancher for example