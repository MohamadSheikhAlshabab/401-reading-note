# Readings: Permissions & Postgresql [URL](https://github.com/MohamadSheikhAlshabab/401-reading-note/blob/master/Read26.md)

## Permissions

  - Authentication or identification by itself is not usually sufficient to gain access to information or code.
  - For that, the entity requesting access must have authorization.
  - Together with authentication and throttling, permissions determine whether a request should be granted or denied access.
  - The simplest style of permission would be to allow access to any authenticated user, and deny access to any unauthenticated user.
  - This corresponds to the IsAuthenticated class in REST framework.
  - A slightly less strict style of permission would be to allow full access to authenticated users, but allow read-only access to unauthenticated users. 
  - This corresponds to the IsAuthenticatedOrReadOnly class in REST framework.
  
  - __How permissions are determined__:
    - Permissions in REST framework are always defined as a list of permission classes.
    - Before running the main body of the view each permission in the list is checked.
    - If any permission check fails an exceptions.PermissionDenied or exceptions.NotAuthenticated exception will be raised, and the main body of the view will not run.
    - When the permissions checks fail either a "403 Forbidden" or a "401 Unauthorized" response will be returned, according to the following rules:

       - The request was successfully authenticated, but permission was denied. — An HTTP 403 Forbidden response will be returned.
       - The request was not successfully authenticated, and the highest priority authentication class does not use WWW-Authenticate headers. — An HTTP 403 Forbidden response will be returned.
       - The request was not successfully authenticated, and the highest priority authentication class does use WWW-Authenticate headers. — An HTTP 401 Unauthorized response, with an appropriate WWW-Authenticate header will be returned.
    
    - __Object level permissions__:
        - REST framework permissions also support object-level permissioning. 
        - Object level permissions are used to determine if a user should be allowed to act on a particular object, which will typically be a model instance.
        - Object level permissions are run by REST framework's generic views when .get_object() is called.
        - As with view level permissions, an exceptions.PermissionDenied exception will be raised if the user is not allowed to act on the given object.
        - This will either raise a PermissionDenied or NotAuthenticated exception, or simply return if the view has the appropriate permissions.
        
    - __Setting the permission policy__:
    
              REST_FRAMEWORK = {
              'DEFAULT_PERMISSION_CLASSES': [
                  'rest_framework.permissions.IsAuthenticated',
                ]
              }
              
           ---
       If not specified, this setting defaults to allowing unrestricted access:

              'DEFAULT_PERMISSION_CLASSES': [
                 'rest_framework.permissions.AllowAny',
              ]
              
          ---
      You can also set the authentication policy on a per-view, or per-viewset basis, using the APIView class-based views.

              from rest_framework.permissions import IsAuthenticated
              from rest_framework.response import Response
              from rest_framework.views import APIView

              class ExampleView(APIView):
                  permission_classes = [IsAuthenticated]

                  def get(self, request, format=None):
                      content = {
                          'status': 'request was permitted'
                      }
                      return Response(content)
                      
                 ---
       Or, if you're using the @api_view decorator with function based views.

                      from rest_framework.decorators import api_view, permission_classes
                      from rest_framework.permissions import IsAuthenticated
                      from rest_framework.response import Response

                      @api_view(['GET'])
                      @permission_classes([IsAuthenticated])
                      def example_view(request, format=None):
                          content = {
                              'status': 'request was permitted'
                          }
                          return Response(content)
                          
                  ---
-   API Reference:
    - __AllowAny__: permission class will allow unrestricted access, regardless of if the request was authenticated or unauthenticated.
    - __IsAuthenticated__: permission class will deny permission to any unauthenticated user, and allow permission otherwise.This permission is suitable if you want your API to only be accessible to registered users.
    - __IsAdminUser__:  permission class will deny permission to any user, unless user.is_staff is True in which case permission will be allowed.This permission is suitable if you want your API to only be accessible to a subset of trusted administrators.
    - __IsAuthenticatedOrReadOnly__: will allow authenticated users to perform any request. Requests for unauthorised users will only be permitted if the request method is one of the "safe" methods; GET, HEAD or OPTIONS.This permission is suitable if you want to your API to allow read permissions to anonymous users, and only allow write permissions to authenticated users.
