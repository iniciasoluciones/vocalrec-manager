# VocalRec Manager API [![Total views](https://sourcegraph.com/api/repos/github.com/pipobscure/NodeJS-AsteriskManager/.counters/views.png)](https://sourcegraph.com/github.com/pipobscure/NodeJS-AsteriskManager)
[![NPM](https://nodei.co/npm/asterisk-manager.png)](https://nodei.co/npm/asterisk-manager/)  

Simply interface to the VocalRec Manager API

## Install

```
$ npm install vocalrec-manager
```

## Usage
```javascript
/**
 * port:  port server
 * host: host server
 * username: username for authentication
 * password: username's password for authentication
 * events: this parameter determines whether events are emited.
 **/
var ami = new require('vocalrec-manager')('port','host','username','password', true);

// In case of any connectiviy problems we got you coverd.
ami.keepConnected();

// Listen for any/all AMI events.
ami.on('managerevent', function(evt) {});

// Listen for specific AMI events. A list of event names can be found at
// https://wiki.asterisk.org/wiki/display/AST/Asterisk+11+AMI+Events
ami.on('hangup', function(evt) {});
ami.on('confbridgejoin', function(evt) {});

// Listen for Action responses.
ami.on('response', function(evt) {});

// Perform an AMI Action. A list of actions can be found at
// https://wiki.asterisk.org/wiki/display/AST/Asterisk+11+AMI+Actions
ami.action({
  'action':'originate',
  'channel':'SIP/myphone',
  'context':'default',
  'exten':1234,
  'priority':1,
  'variable':{
    'name1':'value1',
    'name2':'value2'
  }
}, function(err, res) {});
```

## License

MIT License
-----------

Based on a work Copyright (C) 2010 Brian White <mscdex@gmail.com>, but radically altered thereafter so as to constitute a new work.

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
