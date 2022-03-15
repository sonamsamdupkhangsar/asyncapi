# asyncapi
This is my [AsyncApi](https://www.asyncapi.com/) learning project.

The code is auto generated using [Generator](https://www.npmjs.com/package/@asyncapi/generator) tooling with templating tool from
@asyncapi/nodejs-template.

The asyncapi.yaml is the Streetlights api spefication.
It uses [mosquitto] (https://mosquitto.org/) message broker. The api also specifies the message published for the channel `ligths/measured`.  


## output
Nodejs generated code in output folder

## Generating code

1. Install the [generator](https://github.com/asyncapi/generator) to use it as a command-line tool
```
npm install -g @asyncapi/generator
```
2. Create a directory for your projects and enter it:
```
mkdir streetlights && cd "$_"
```
3. Create asyncapi.yaml by copying the asyncapi.yaml from root of repo.
4. Trigger generation of the Node.js code
```
cp ../asyncapi.yaml .;
ag asyncapi.yaml @asyncapi/nodejs-template -o output -p server=mosquitto
```
5. cd to generated output folder
```
cd output && ls
```

## Running your code
6. install depdencies 
```
npm install
```
7. start app
```
npm start
```
8.  Open new terminal, install mqtt library
```
npm install mqtt -g
```
9.  send valid message to app
```
mqtt pub -t 'light/measured' -h 'test.mosquitto.org' -m '{"id": 1, "lumens": 3, "sentAt": "2017-06-07T12:34:32.000Z"}'
```
10. send invalid message
```
mqtt pub -t 'light/measured' -h 'test.mosquitto.org' -m '{"id": 1, "lumens": "3", "sentAt": "2017-06-07T12:34:32.000Z"}'
```

