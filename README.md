node-mail-stripper
==================

Strip signatures and previous emails from email bodies

# install
`npm install node-mail-stripper`

# use
## simple use
```javascript
    const MailStripper = require("mail-stripper");
    stripper = new MailStripper({});
    message = stripper.parse(mail);
```

MailStripper will parse the mail line by line. Whenever a line matches one of the patterns, it will be treated as a signature and the parsing of the email will stop.
The output message will contain all the lines before that first 'signature' line

## add custom rules
```javascript
    stripper = new MailStripper({
        patterns: [
            /\d{7}/,
            /^####/,
        ]});
    message = stripper.parse(mail);
```

## advanced signature parsing
If your provide the name of the sender of the message, MailStripper will detect a line containing only that name and spaces as a signature.
```javascript
    stripper = new MailStripper();
    message = stripper.parse(mail, 'martin saint-macary');
```


# contribute
If you find yourself adding rules that could be relevant to other projects, please add them directly to the source and send me a pull request or just create an issue and I'll add them myself

## test
`npm test`

## build
`coffee -c -o . src/mail-stripper.coffee`




