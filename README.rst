Django Ajax Crawling
====================

Django application to make your AJAX application crawlable through django.
This app is mainly based in this document https://developers.google.com/webmasters/ajax-crawling/docs/getting-started


Configuration
=============

#. Add the following middleware to your project's ``settings.py`` file::

    MIDDLEWARE_CLASSES = (
        # ...
        'django_ajax_crawling.middleware.HtmlSnapshotMiddleware',
        # ...
    )


#. Create another urls.conf file (different from default project's urls.conf file), which will contain each ajax url to be crawled::

    from django.conf.urls import patterns, url

    urlpatterns = patterns('',
        url(r'^object/(?P<object>.*)/$', 'app.views_html_snapshot.object_details'),

    )


#. Define configuration option to specify location of previous urls.conf file. i.e:

    AJAX_CRAWLING_URLCONF = 'project.urls_ajax_crawling'

