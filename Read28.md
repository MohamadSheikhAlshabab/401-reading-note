# API Deployment  [URL](https://github.com/MohamadSheikhAlshabab/401-reading-note/blob/master/Read28.md)

## Configuring Django Settings: Best Practices

  - Sensitive data. You have SECRET_KEY in each Django project. On top of this there can be DB passwords and tokens for third-party APIs like Amazon or Twitter. This data cannot be stored in VCS.
  - Sharing settings between team members. You need a general approach to eliminate human error when working with the settings. For example, a developer may add a third-party app or some API integration and fail to add specific settings. On large (or even mid-size) projects, this can cause real issues.
  - Django settings are a Python code. This is a curse and a blessing at the same time. It gives you a lot of flexibility, but can also be a problem – instead of key-value pairs, settings.py can have a very tricky logic.
  
  - __Setting Configuration: Different Approaches__:
    - There is no built-in universal way to configure Django settings without hardcoding them.
    
    - settings_local.py: 
     - This is the oldest method. I used it when I was configuring a Django project on a production server for the first time. 
     
                            settings.py file:
                            ALLOWED_HOSTS = ['example.com']
                            DEBUG = False
                            DATABASES = {
                                'default': {
                                    'ENGINE': 'django.db.backends.postgresql',
                                    'NAME': 'production_db',
                                    'USER': 'user',
                                    'PASSWORD': 'password',
                                    'HOST': 'db.example.com',
                                    'PORT': '5432',
                                    'OPTIONS': {
                                        'sslmode': 'require'
                                    }
                                }
                            }

                            ...

                            from .settings_local import *
                            
                            
        - settings_local.py file:

                          ALLOWED_HOSTS = ['localhost']
                          DEBUG = True
                          DATABASES = {
                              'default': {
                                  'ENGINE': 'django.db.backends.postgresql',
                                  'NAME': 'local_db',
                                  'HOST': '127.0.0.1',
                                  'PORT': '5432',
                              }
                          }
                          
         - Pros: Secrets not in VCS.
         -  Cons:
            - settings_local.py is not in VCS, so you can lose some of your Django environment settings.
            - The Django settings file is a Python code, so settings_local.py can have some non-obvious logic.
            - You need to have settings_local.example (in VCS) to share the default configurations for developers.
            
        ---    
      - Separate settings file for each environment
      
          settings/local.py:

                                      from .base import *


                                      ALLOWED_HOSTS = ['localhost']
                                      DEBUG = True
                                      DATABASES = {
                                          'default': {
                                              'ENGINE': 'django.db.backends.postgresql',
                                              'NAME': 'local_db',
                                              'HOST': '127.0.0.1',
                                              'PORT': '5432',
                                          }
                                      }
                                      
          - in terminal type this command: `python manage.py runserver --settings=settings.local`
          - Pros:
            - All environments are in VCS.
            - It’s easy to share settings between developers.
          - Cons:
            - You need to find a way to handle secret passwords and tokens.
            - “Inheritance” of settings can be hard to trace and maintain.
----
## How Does SSH Work
  - What is SSH:
    - SSH, or Secure Shell, is a remote administration protocol that allows users to control and modify their remote servers over the Internet.
    - The service was created as a secure replacement for the unencrypted Telnet and uses cryptographic techniques to ensure that all communication to and from the remote server happens in an encrypted manner.
    - It provides a mechanism for authenticating a remote user, transferring inputs from the client to the host, and relaying the output back to the client.
  - How Does SSH Work:
    - If you’re using Linux or Mac, then using SSH is very simple. If you use Windows, you will need to utilize an SSH client to open SSH connections.
    - The most popular SSH client is PuTTY, which you can learn more about here.
    - For Mac and Linux users, head over to your terminal program and then follow the procedure below:
    - The SSH command consists of 3 distinct parts:
    - `ssh {user}@{host}`
    -  There are three different encryption technologies used by SSH:
      - 1 - Symmetrical encryption
        - Symmetric encryption is a form of encryption where a secret key is used for both encryption and decryption of a message by both the client and the host.
        - Effectively, any one possessing the key can decrypt the message being transferred.
        - ![img](https://www.hostinger.com/tutorials/wp-content/uploads/sites/2/2017/07/symmetric-encryption-ssh-tutorial.jpg)
      - 2 - Asymmetrical encryption
        - Unlike symmetrical encryption, asymmetrical encryption uses two separate keys for encryption and decryption.
        - These two keys are known as the public key and the private key. Together, both these keys form a public-private key pair.
        - ![img](https://www.hostinger.com/tutorials/wp-content/uploads/sites/2/2017/07/asymmetric-encryption.jpg)
      - 3 - Hashing.
           - One-way hashing is another form of cryptography used in Secure Shell Connections. 
           - One-way-hash functions differ from the above two forms of encryption in the sense that they are never meant to be decrypted.
           - They generate a unique value of a fixed length for each input that shows no clear trend which can exploited. This makes them practically impossible to reverse.
           - ![img](https://www.hostinger.com/tutorials/wp-content/uploads/sites/2/2017/07/ssh-tutorial-hash.jpg)
           
     - How Does SSH Work with These Encryption Techniques:
        - The way SSH works is by making use of a client-server model to allow for authentication of two remote systems and encryption of the data that passes between them.
        - SSH operates on TCP port 22 by default (though this can be changed if needed). 
        - The host (server) listens on port 22 (or any other SSH assigned port) for incoming connections. 
        - It organizes the secure connection by authenticating the client and opening the correct shell environment if the verification is successful.
        - ![img](https://www.hostinger.com/tutorials/wp-content/uploads/sites/2/2017/07/ssh-client-and-server.jpg)

          
