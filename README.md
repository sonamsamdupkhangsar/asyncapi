# asyncapi
This is my AsyncApi learning project.

## output
Nodejs generated code in output folder

## Generating code

1. Install the generator to use it as a command-line tool
```npm install -g @asyncapi/generator```
2. Create a directory for your projects and enter it:
```mkdir streetlights && cd "$_"```
3. Create asyncapi.yaml
4. Trigger generation of the Node.js code
```ag asyncapi.yaml @asyncapi/nodejs-template -o output -p server=mosquitto```
5. cd to generated output folder
```cd output && ls```

## Running your code
1. install depdencies 
```npm install`
2. start app
```npm start```
3.  Open new terminal
```npm install mqtt -g```
4.  send valid message to app
```mqtt pub -t 'light/measured' -h 'test.mosquitto.org' -m '{"id": 1, "lumens": 3, "sentAt": "2017-06-07T12:34:32.000Z"}'```
5. send invalid message
```mqtt pub -t 'light/measured' -h 'test.mosquitto.org' -m '{"id": 1, "lumens": "3", "sentAt": "2017-06-07T12:34:32.000Z"}'```

