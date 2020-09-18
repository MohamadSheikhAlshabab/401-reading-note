# Readings: Intro to Django [URL](https://github.com/MohamadSheikhAlshabab/401-reading-note/blob/master/Read20.md)

## Getting started with Django
   ### Intro to Django
   - __Object-relational mapper__:
    

      ```
      class Band(models.Model):
      """A model of a rock band."""
      name = models.CharField(max_length=200)
      can_rock = models.BooleanField(default=True)

      class Member(models.Model):
          """A model of a rock band member."""
          name = models.CharField("Member's name", max_length=200)
          instrument = models.CharField(choices=(
                  ('g', "Guitar"),
                  ('b', "Bass"),
                  ('d', "Drums"),
              ),
              max_length=1
          )
          band = models.ForeignKey("Band")
      ```
  - __URLs and views__: A clean, elegant URL scheme is an important detail in a high-quality Web application. 
      - Django encourages beautiful URL design and doesn’t put any cruft in URLs, like .php or .asp.
      - To design URLs for an application, you create a Python module called a URLconf.
      - Like a table of contents for your app, it contains a simple mapping between URL patterns and your views.
      ```
      from django.urls import path
      from . import views
      urlpatterns = [
          path('bands/', views.band_listing, name='band-list'),
          path('bands/<int:band_id>/', views.band_detail, name='band-detail'),
          path('bands/search/', views.band_search, name='band-search'),
      ]
      ```
      ```
      from django.shortcuts import render

      def band_listing(request):
          """A view of all bands."""
          bands = models.Band.objects.all()
          return render(request, 'bands/band_listing.html', {'bands': bands})
      ```
   - __Templates__: Django’s template language is designed to strike a balance between power and ease.
     - It’s designed to feel comfortable and easy-to-learn to those used to working with HTML, like designers and front-end developers.
     - But it is also flexible and highly extensible, allowing developers to augment the template language as needed.
     ```
       <html>
        <head>
          <title>Band Listing</title>
        </head>
        <body>
          <h1>All Bands</h1>
          <ul>
          {% for band in bands %}
            <li>
              <h2><a href="{{ band.get_absolute_url }}">{{ band.name }}</a></h2>
              {% if band.can_rock %}<p>This band can rock!</p>{% endif %}
            </li>
          {% endfor %}
          </ul>
        </body>
      </html>
     ```
  - __Forms__: Django provides a powerful form library that handles rendering forms as HTML, validating user-submitted data, and converting that data to native Python types.
    - Django also provides a way to generate forms from your existing models and use those forms to create and update data.
    ```
    from django import forms

    class BandContactForm(forms.Form):
        subject = forms.CharField(max_length=100)
        message = forms.CharField()
        sender = forms.EmailField()
        cc_myself = forms.BooleanField(required=False)
    ```
    
 - __Authentication__: Django comes with a full-featured and secure authentication system. It handles user accounts, groups, permissions and cookie-based user sessions.
    - This lets you easily build sites that let users to create accounts and safely log in/out.
    ```
    from django.contrib.auth.decorators import login_required
    from django.shortcuts import render

    @login_required
    def my_protected_view(request):
        """A view that can only be accessed by logged-in users"""
        return render(request, 'protected.html', {'current_user': request.user})
    ```
 - __Admin__: One of the most powerful parts of Django is its automatic admin interface.
   - It reads metadata in your models to provide a powerful and production-ready interface that content producers can immediately use to start managing content on your site.
   - It’s easy to set up and provides many hooks for customization.
   
   ```
   from django.contrib import admin
   from bands.models import Band, Member

   class MemberAdmin(admin.ModelAdmin):
       """Customize the look of the auto-generated admin for the Member model"""
       list_display = ('name', 'instrument')
       list_filter = ('band',)
       
   admin.site.register(Band)  # Use the default options
   admin.site.register(Member, MemberAdmin)  # Use the customized options
   ```
- __Internationalization__: Django offers full support for translating text into different languages, plus locale-specific formatting of dates, times, numbers and time zones.
   - It lets developers and template authors specify which parts of their apps should be translated or formatted for local languages and cultures, and it uses these hooks to localize Web applications for particular users according to their preferences.
   ```
   from django.shortcuts import render
  from django.utils.translation import gettext

  def homepage(request):
      """
      Shows the homepage with a welcome message that is translated in the
      user's language.
      """
      message = gettext('Welcome to our site!')
      return render(request, 'homepage.html', {'message': message})
   ```
   ```
   {% load i18n %}
    <html>
      <head>
        <title>{% trans 'Homepage - Hall of Fame' %}</title>
      </head>
      <body>
        {# Translated in the view: #}
        <h1>{{ message }}</h1>
        <p>
          {% blocktrans count member_count=bands.count %}
          Here is the only band in the hall of fame:
          {% plural %}
          Here are all the {{ member_count }} bands in the hall of fame:
          {% endblocktrans %}
        </p>
        <ul>
        {% for band in bands %}
          <li>
            <h2><a href="{{ band.get_absolute_url }}">{{ band.name }}</a></h2>
            {% if band.can_rock %}<p>{% trans 'This band can rock!' %}</p>{% endif %}
          </li>
        {% endfor %}
        </ul>
      </body>
    </html>
   ```
---
## How Django Works Behind the Scenes:
   - Django is a Python-based web framework used by millions of developers and billions of consumers through popular apps like Instagram.
   - It is open source, meaning the code is available for free on Github and can be downloaded onto any developer’s computer and used alongside the official documentation.
   - Django was originally developed at the Lawrence Journal-World newspaper by Adrian Holovaty, Simon Willison, and Jacob Kaplan-Moss.
   - The code was open-sourced in 2005 and developers immediately started making contributions to the codebase.
   - Django’s code is open source and available to all. Django’s organization is managed by a non-profit, the DSF, with a miniscule budget.
   - And Django code is lead by a core team of volunteers, two paid Django Fellows, and a larger group of contributors.
---
## Django introduction:
  - __What is Django?__:
    - Django is a high-level Python web framework that enables rapid development of secure and maintainable websites.
    - Built by experienced developers, Django takes care of much of the hassle of web development, so you can focus on writing your app without needing to reinvent the wheel. 
    - It is free and open source, has a thriving and active community, great documentation, and many options for free and paid-for support. 
    - Django helps you write software that is:
      - 1 - Complete
      - 2 - Versatile
      - 3 - Secure
      - 4 - Scalable
      - 5 - Maintainable
      - 6 - Portable
