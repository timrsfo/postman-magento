# postman-magento

## dockerized-magento
I am testing against dockerized-magento which was forked from:
[all9lives/dockerized-magento](https://github.com/all9lives/dockerized-magento)
forked from 
[andreaskoch/dockerized-magento](https://github.com/andreaskoch/dockerized-magento)
dockerized-magento is running locally on a Ubuntu 14.04 host

Magento 1.9x, REST with OAuth 1.0a

You will need to create:
Consumer Key
Consumer Secret
Token
Token Secret

## Getting up to speed on postman
Postman is a Chrome application used for testing RESTful APIs

A google search will direct you to lots of information on postman

I found the following link to be very helpful to get upto speed on
creating collections, environments and variable substitution:
[POSTMAN RESTful API testing app demo](https://www.youtube.com/watch?v=O6la-NJYiu8)

In the end you will create collections and environments.
Collections allow you to group commands targeting a particular feature.
The key is to use variable substitution combined with environments. 
You declare multiple environments, TEST, QA, DEV, PROD, etc. You create a set
of variables that will be used in your collections. Each environment duplicates
the same variable(s) but with values specific to it, e.g. base-url:
TEST base-url http://my-test-env/..., PROD base-url http://my-prod/...

The collection references the variable:
{{base-url}}/..
In this case swaping the environment changes the server location. See above link 
for more details


## Postman Newman (CLI)
Postman has a counterpart, called newman. Newman can be used to run collections
from the commandline (no GUI). The Postman app allows you to save your collections
environments to json files. These can then be used be Newman to run your tests.

newman -c MagentoCustomers-160910.postman-collection.json -e MAG-Test.postman-environment.json

## Postman Newman and Jenkins
Collections/Environments can also be used in your CI environment, such as Jenkins.
The following link helped me to figure out how this is done:
[How to write powerful automated API tests with Postman, Newman and Jenkins](http://blog.getpostman.com/2015/09/03/how-to-write-powerful-automated-api-tests-with-postman-newman-and-jenkins/)

Note: The link above uses a out-of-date commandline:
newman -c jenkins-demo.postman-collection --exitCode 1
I found the --exitCode 1 does not work and substituted the command shown above.
