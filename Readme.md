# devserver in secure mode


Step 1

Define a STATIC_ROOT and MEDIA_ROOT path in settings.py.

Code: settings.py


                STATIC_URL = '/static/'

                MEDIA_URL = '/media/'

  

                if DEBUG:

                      STATICFILES_DIRS = [os.path.join(BASE_DIR, 'static')]

                else:

                      STATIC_ROOT = os.path.join(BASE_DIR, 'static')
  
                MEDIA_ROOT = os.path.join(BASE_DIR, 'media')
                
                
 
Step 2

Code: urls.py


                from django.urls import re_path as url
                from django.conf import settings
                from django.views.static import serve

                urlpatterns = [
                      url(r'^media/(?P<path>.*)$', serve,{'document_root': settings.MEDIA_ROOT}),
                      url(r'^static/(?P<path>.*)$', serve,{'document_root': settings.STATIC_ROOT}),
                ]
                
                
                
