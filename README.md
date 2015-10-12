# mailsender:

Simple command line mail sender. Used to send messages or HTML page to a list of users. The program read content from stdin and send it as HTML code to the target mail address.

## Usage:

```
$ mailsender [options] [arguments]
```

### Options:

- -h, --help:
    Print this help message.

- -v, --version:
    Print version information.

- -t <to_address>:
    Set single target mail address.

- --to_list="to_address1[,to_address2 ...]":
    Set a list of target mail addresses, separate with comma.

- -H, --host="mail.host.server":
    Set the mail host server

- -f, --sender="you@your.mail.host.domain":
    Set the sender mail address.

- -u "username", --username="username":
    Set the username to be shown on the mail.

- -p "mailbox login password", --passwd="mailbox login password":
    Set the login password of the sender mailbox.
    ** If the this option is not set, the program will ask for password when running. **

- -s "mail subject", --subject="mail subject":
    Set the subject of the mail.

- -d, --debug:
    Enable debug output.
    ** ATTENTION: If you enter password from stdin, the password will also be output! **

- -c "config.json", --config="config.json":
    Read from config file and set the value of the variables with it.
    ** ATTENTION: If the variable is also set in the command line argument, the last value will be used! **

### Examples:

1. read from stdin and send to the target mail address
    
    ```
    $ mailsender -t "receive@foo.bar" -H "mail.foo.bar" -f "from@foo.bar" -s "hello" -u "kagurazaka kirie"
    ```

2. send a html file "foo.html" to a list of receivers configured with config file "config.json"

    ```
    $ cat foo.html | mailsender -c config.json -s "content of foo.html"
    ```
    
## Config file:

The config file uses json syntax to set the variables. You can config the following variables.

- to_list (list): Same with `to_list` option.
- host (domain): Same with `host` option.
- sender (mail address): Same with `sender` option.
- username (string): Same with `username` option.
- passwd (string): Same with `passwd` option.
- subject (string): Same with `subject` option.

### Example:

```
{
  "to_list"     : ["receive1@foo.bar", "receive2@foo.bar", "receive3@foo.bar"],
  "host"        : "mail.foo.bar",
  "sender"      : "from@foo.bar",
  "username"    : "kagurazaka kirie",
  "subject"     : "hello"
}
```

## Dependence:

- Python 2.7
- Python - smtplib
- Python - sys
- Python - email
- Python - getopt
- Python - getpass
- Python - json
