# Tcp-Server
If the server receives 1 Return upper case, return lower case if 2, return revise if 3.

# This code will work on python 

from socket import*
Port=9999
server =socket(AF_INET,SOCK_STREAM)
server.bind(('127.0.0.1',Port))
server.listen(1)
print "[*] Started listening on "":",Port
while 1: 
    csocket,addr = server.accept()
    print "[*] Got a connection from", addr
    csocket.send('OK. Type Your Sentence Now')
    sentence = csocket.recv(1024)
    csocket.send(" Enter 1)upper \n 2) lower\n 3)reverse\n\n")
    choice = csocket.recv(1024)
    
    if (choice ==1):
        modtext =sentence.upper()
    elif (choice ==2):
        modtext =sentence.lower()
    elif (choice == 3):
        modtext=sentence[::-1]
    else:
        modtext= 'Error....'
    csocket.send(modtext)
    csocket.close()
    
