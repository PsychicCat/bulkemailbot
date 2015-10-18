# bulkemailbot
A simple email client for Node.js. Quickly send personalized emails imported from a CSV file.

GitHub repository: [github.com/PsychicCat/bulkemailbot][repo]
Dependencies: [Nodemailer][nodemailer], [csvtojson][csvtojson].

## License
ISC, open source. See LICENSE file.

## install via NPM:
    npm install bulkemailbot

## or install via GitHub:
    git clone https://github.com/PsychicCat/bulkemailbot
    cd bulkemailbot
    npm install

## or download the latest source:
*   [zip download][repo-zip]

## Require the module
    var BulkEmailBot = require('bulkemailbot');
If not installed via NPM, provide the path to lib/bulkemailbot.js

## Create an instance of the client
    var userEmail = 'YOUR EMAIL ADDRESS',
        userPassword = 'YOUR PASSWORD',
        userService = 'Gmail', //see Nodemailer for other supported email services
        userName = 'yourFirstName yourLastName',
        user = new BulkEmailBot(userName, userEmail, userService, userPassword);

## Create a message template
Note: only $fName (firstName) is supported at this time.

    var message = {
        subject: 'Hey',
        template: 'Hi $fName, thanks for the interview!'
    }

## Prepare recipient list in CSV file 
*   Example: [recipients.csv][csv]

## Send bulk emails!

### user.bulkSend(csvFile, message, callback)
Example:

    user.bulkSend('./recipients.csv', message, function(err, data){
        if(err){
            console.log(err);
        } else {
            console.log('Message sent to ', data.envelope.to);
        }
    });
Response:
    
    Message sent to  [ 'email@email.com' ]
    Message sent to  [ 'email2@email.com' ]
    Message sent to  [ 'telzrowb@gmail.com' ]
 
    
    
    




[repo]: https://github.com/PsychicCat/bulkemailbot
[repo-zip]: https://github.com/PsychicCat/bulkemailbot/archive/master.zip
[nodemailer]: https://github.com/andris9/Nodemailer
[csvtojson]: https://github.com/Keyang/node-csvtojson
[csv]: https://github.com/PsychicCat/bulkemailbot/blob/master/recipients.csv