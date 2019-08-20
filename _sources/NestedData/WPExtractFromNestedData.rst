..  Copyright (C)  Paul Resnick.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. _debug_nested_chap:

.. qnum::
   :prefix: WPNested-1-
   :start: 1

👩‍💻 Extracción de Datos Anidados
====================================

Un problema común, especialmente cuando se trata de datos devueltos desde un sitio web, es extraer ciertos elementos de
dentro de una estructura de datos anidada. En principio, no hay nada más difícil sobre sacar algo de lo más profundo de
una estructura de datos anidada: con listas, usa [] para indexar o un bucle for para obtenerlas todas; con diccionarios, obtienes
el valor asociado con una clave particular usando [] o iterar a través de todas las claves, accediendo al valor de cada una.
Pero es fácil perderse en el proceso y pensar que ha extraído algo diferente de lo que realmente tienes. Debido a esto, hemos
creado una técnica utilizable para ayudarlo durante el proceso de depuración

Siga el sistema descrito a continuación y tendrá éxito con la extracción de datos anidados. El proceso involucra el
siguientes pasos:

1. Comprender el objeto de datos anidados.
2. Extraer un objeto en el siguiente nivel hacia abajo.
3. Repita el proceso con el objeto extraído.

Entender. Extraer. Repetir.

Para ilustrar esto, veremos cómo extraer información de los datos formateados de manera tal que la API de Twitter la devuelva.
Este diccionario anidado resulta de consultar Twitter, pidiendo tres tweets emparejando "Universidad de Michigan".
Como verá, es una estructura de datos bastante desalentadora, incluso cuando se imprime con buena sangría como se muestra a continuación.

.. activecode:: ac300_1_1

   res = {
     "search_metadata": {
       "count": 3, 
       "completed_in": 0.015, 
       "max_id_str": "536624519285583872", 
       "since_id_str": "0", 
       "next_results": "?max_id=536623674942439424&q=University%20of%20Michigan&count=3&include_entities=1", 
       "refresh_url": "?since_id=536624519285583872&q=University%20of%20Michigan&include_entities=1", 
       "since_id": 0, 
       "query": "University+of+Michigan", 
       "max_id": 536624519285583872
     }, 
     "statuses": [
       {
         "contributors": None, 
         "truncated": False, 
         "text": "RT @mikeweber25: I'm decommiting from the university of Michigan thank you Michigan for the love and support I'll remake my decision at the\u2026", 
         "in_reply_to_status_id": None, 
         "id": 536624519285583872, 
         "favorite_count": 0, 
         "source": "<a href=\"http://twitter.com/download/iphone\" rel=\"nofollow\">Twitter for iPhone</a>", 
         "retweeted": False, 
         "coordinates": None, 
         "entities": {
           "symbols": [], 
           "user_mentions": [
             {
               "id": 1119996684, 
               "indices": [
                 3, 
                 15
               ], 
               "id_str": "1119996684", 
               "screen_name": "mikeweber25", 
               "name": "Mikey"
             }
           ], 
           "hashtags": [], 
           "urls": []
         }, 
         "in_reply_to_screen_name": None, 
         "in_reply_to_user_id": None, 
         "retweet_count": 2014, 
         "id_str": "536624519285583872", 
         "favorited": False, 
         "retweeted_status": {
           "contributors": None, 
           "truncated": False, 
           "text": "I'm decommiting from the university of Michigan thank you Michigan for the love and support I'll remake my decision at the army bowl", 
           "in_reply_to_status_id": None, 
           "id": 536300265616322560, 
           "favorite_count": 1583, 
           "source": "<a href=\"http://twitter.com/download/iphone\" rel=\"nofollow\">Twitter for iPhone</a>", 
           "retweeted": False, 
           "coordinates": None, 
           "entities": {
             "symbols": [], 
             "user_mentions": [], 
             "hashtags": [], 
             "urls": []
           }, 
           "in_reply_to_screen_name": None, 
           "in_reply_to_user_id": None, 
           "retweet_count": 2014, 
           "id_str": "536300265616322560", 
           "favorited": False, 
           "user": {
             "follow_request_sent": False, 
             "profile_use_background_image": True, 
             "profile_text_color": "666666", 
             "default_profile_image": False, 
             "id": 1119996684, 
             "profile_background_image_url_https": "https://abs.twimg.com/images/themes/theme9/bg.gif", 
             "verified": False, 
             "profile_location": None, 
             "profile_image_url_https": "https://pbs.twimg.com/profile_images/534465900343083008/A09dIq1d_normal.jpeg", 
             "profile_sidebar_fill_color": "252429", 
             "entities": {
               "description": {
                 "urls": []
               }
             }, 
             "followers_count": 5444, 
             "profile_sidebar_border_color": "FFFFFF", 
             "id_str": "1119996684", 
             "profile_background_color": "C0DEED", 
             "listed_count": 36, 
             "is_translation_enabled": False, 
             "utc_offset": None, 
             "statuses_count": 6525, 
             "description": "Mike Weber (U.S Army All American) DETROIT CTSENIOR State Champion", 
             "friends_count": 693, 
             "location": "", 
             "profile_link_color": "0084B4", 
             "profile_image_url": "http://pbs.twimg.com/profile_images/534465900343083008/A09dIq1d_normal.jpeg", 
             "following": False, 
             "geo_enabled": False, 
             "profile_banner_url": "https://pbs.twimg.com/profile_banners/1119996684/1416261575", 
             "profile_background_image_url": "http://abs.twimg.com/images/themes/theme9/bg.gif", 
             "name": "Mikey", 
             "lang": "en", 
             "profile_background_tile": False, 
             "favourites_count": 1401, 
             "screen_name": "mikeweber25", 
             "notifications": False, 
             "url": None, 
             "created_at": "Fri Jan 25 18:45:53 +0000 2013", 
             "contributors_enabled": False, 
             "time_zone": None, 
             "protected": False, 
             "default_profile": False, 
             "is_translator": False
           }, 
           "geo": None, 
           "in_reply_to_user_id_str": None, 
           "lang": "en", 
           "created_at": "Sat Nov 22 23:28:41 +0000 2014", 
           "in_reply_to_status_id_str": None, 
           "place": None, 
           "metadata": {
             "iso_language_code": "en", 
             "result_type": "recent"
           }
         }, 
         "user": {
           "follow_request_sent": False, 
           "profile_use_background_image": True, 
           "profile_text_color": "333333", 
           "default_profile_image": False, 
           "id": 2435537208, 
           "profile_background_image_url_https": "https://abs.twimg.com/images/themes/theme1/bg.png", 
           "verified": False, 
           "profile_location": None, 
           "profile_image_url_https": "https://pbs.twimg.com/profile_images/532694075947110400/oZEP5XNQ_normal.jpeg", 
           "profile_sidebar_fill_color": "DDEEF6", 
           "entities": {
             "description": {
               "urls": []
             }
           }, 
           "followers_count": 161, 
           "profile_sidebar_border_color": "C0DEED", 
           "id_str": "2435537208", 
           "profile_background_color": "C0DEED", 
           "listed_count": 0, 
           "is_translation_enabled": False, 
           "utc_offset": None, 
           "statuses_count": 524, 
           "description": "Delasalle '17 Baseball & Football.", 
           "friends_count": 255, 
           "location": "", 
           "profile_link_color": "0084B4", 
           "profile_image_url": "http://pbs.twimg.com/profile_images/532694075947110400/oZEP5XNQ_normal.jpeg", 
           "following": False, 
           "geo_enabled": False, 
           "profile_banner_url": "https://pbs.twimg.com/profile_banners/2435537208/1406779364", 
           "profile_background_image_url": "http://abs.twimg.com/images/themes/theme1/bg.png", 
           "name": "Andrew Brooks", 
           "lang": "en", 
           "profile_background_tile": False, 
           "favourites_count": 555, 
           "screen_name": "31brooks_", 
           "notifications": False, 
           "url": None, 
           "created_at": "Wed Apr 09 14:34:41 +0000 2014", 
           "contributors_enabled": False, 
           "time_zone": None, 
           "protected": False, 
           "default_profile": True, 
           "is_translator": False
         }, 
         "geo": None, 
         "in_reply_to_user_id_str": None, 
         "lang": "en", 
         "created_at": "Sun Nov 23 20:57:10 +0000 2014", 
         "in_reply_to_status_id_str": None, 
         "place": None, 
         "metadata": {
           "iso_language_code": "en", 
           "result_type": "recent"
         }
       }, 
       {
         "contributors": None, 
         "truncated": False, 
         "text": "RT @Plantedd: The University of Michigan moved a big Bur Oak yesterday. 65ft tall. 350+ tons. http://t.co/v2Y6vl3f9e", 
         "in_reply_to_status_id": None, 
         "id": 536624216305848320, 
         "favorite_count": 0, 
         "source": "<a href=\"http://tapbots.com/tweetbot\" rel=\"nofollow\">Tweetbot for i\u039fS</a>", 
         "retweeted": False, 
         "coordinates": None, 
         "entities": {
           "symbols": [], 
           "user_mentions": [
             {
               "id": 462890283, 
               "indices": [
                 3, 
                 12
               ], 
               "id_str": "462890283", 
               "screen_name": "Plantedd", 
               "name": "David Wong"
             }
           ], 
           "hashtags": [], 
           "urls": [], 
           "media": [
             {
               "source_status_id_str": "526276522374889472", 
               "expanded_url": "http://twitter.com/Plantedd/status/526276522374889472/photo/1", 
               "display_url": "pic.twitter.com/v2Y6vl3f9e", 
               "url": "http://t.co/v2Y6vl3f9e", 
               "media_url_https": "https://pbs.twimg.com/media/B021tLsIYAADq21.jpg", 
               "source_status_id": 526276522374889472, 
               "id_str": "526276519308845056", 
               "sizes": {
                 "small": {
                   "h": 191, 
                   "resize": "fit", 
                   "w": 340
                 }, 
                 "large": {
                   "h": 576, 
                   "resize": "fit", 
                   "w": 1024
                 }, 
                 "medium": {
                   "h": 337, 
                   "resize": "fit", 
                   "w": 600
                 }, 
                 "thumb": {
                   "h": 150, 
                   "resize": "crop", 
                   "w": 150
                 }
               }, 
               "indices": [
                 94, 
                 116
               ], 
               "type": "photo", 
               "id": 526276519308845056, 
               "media_url": "http://pbs.twimg.com/media/B021tLsIYAADq21.jpg"
             }
           ]
         }, 
         "in_reply_to_screen_name": None, 
         "in_reply_to_user_id": None, 
         "retweet_count": 27, 
         "id_str": "536624216305848320", 
         "favorited": False, 
         "retweeted_status": {
           "contributors": None, 
           "truncated": False, 
           "text": "The University of Michigan moved a big Bur Oak yesterday. 65ft tall. 350+ tons. http://t.co/v2Y6vl3f9e", 
           "in_reply_to_status_id": None, 
           "id": 526276522374889472, 
           "favorite_count": 25, 
           "source": "<a href=\"http://twitter.com/download/iphone\" rel=\"nofollow\">Twitter for iPhone</a>", 
           "retweeted": False, 
           "coordinates": None, 
           "entities": {
             "symbols": [], 
             "user_mentions": [], 
             "hashtags": [], 
             "urls": [], 
             "media": [
               {
                 "expanded_url": "http://twitter.com/Plantedd/status/526276522374889472/photo/1", 
                 "display_url": "pic.twitter.com/v2Y6vl3f9e", 
                 "url": "http://t.co/v2Y6vl3f9e", 
                 "media_url_https": "https://pbs.twimg.com/media/B021tLsIYAADq21.jpg", 
                 "id_str": "526276519308845056", 
                 "sizes": {
                   "small": {
                     "h": 191, 
                     "resize": "fit", 
                     "w": 340
                   }, 
                   "large": {
                     "h": 576, 
                     "resize": "fit", 
                     "w": 1024
                   }, 
                   "medium": {
                     "h": 337, 
                     "resize": "fit", 
                     "w": 600
                   }, 
                   "thumb": {
                     "h": 150, 
                     "resize": "crop", 
                     "w": 150
                   }
                 }, 
                 "indices": [
                   80, 
                   102
                 ], 
                 "type": "photo", 
                 "id": 526276519308845056, 
                 "media_url": "http://pbs.twimg.com/media/B021tLsIYAADq21.jpg"
               }
             ]
           }, 
           "in_reply_to_screen_name": None, 
           "in_reply_to_user_id": None, 
           "retweet_count": 27, 
           "id_str": "526276522374889472", 
           "favorited": False, 
           "user": {
             "follow_request_sent": False, 
             "profile_use_background_image": True, 
             "profile_text_color": "333333", 
             "default_profile_image": False, 
             "id": 462890283, 
             "profile_background_image_url_https": "https://abs.twimg.com/images/themes/theme1/bg.png", 
             "verified": False, 
             "profile_location": None, 
             "profile_image_url_https": "https://pbs.twimg.com/profile_images/1791926707/Plantedd_Logo__square__normal.jpg", 
             "profile_sidebar_fill_color": "DDEEF6", 
             "entities": {
               "url": {
                 "urls": [
                   {
                     "url": "http://t.co/ZOnsCHvoKt", 
                     "indices": [
                       0, 
                       22
                     ], 
                     "expanded_url": "http://www.plantedd.com", 
                     "display_url": "plantedd.com"
                   }
                 ]
               }, 
               "description": {
                 "urls": []
               }
             }, 
             "followers_count": 2598, 
             "profile_sidebar_border_color": "C0DEED", 
             "id_str": "462890283", 
             "profile_background_color": "C0DEED", 
             "listed_count": 61, 
             "is_translation_enabled": False, 
             "utc_offset": 0, 
             "statuses_count": 8157, 
             "description": "Hello, I'm the supervillain behind Plantedd. We're an online market for plant lovers plotting to take over the world by making it simple to find and buy plants.", 
             "friends_count": 2664, 
             "location": "UK", 
             "profile_link_color": "0084B4", 
             "profile_image_url": "http://pbs.twimg.com/profile_images/1791926707/Plantedd_Logo__square__normal.jpg", 
             "following": False, 
             "geo_enabled": False, 
             "profile_banner_url": "https://pbs.twimg.com/profile_banners/462890283/1398254314", 
             "profile_background_image_url": "http://abs.twimg.com/images/themes/theme1/bg.png", 
             "name": "David Wong", 
             "lang": "en", 
             "profile_background_tile": False, 
             "favourites_count": 371, 
             "screen_name": "Plantedd", 
             "notifications": False, 
             "url": "http://t.co/ZOnsCHvoKt", 
             "created_at": "Fri Jan 13 13:46:46 +0000 2012", 
             "contributors_enabled": False, 
             "time_zone": "Edinburgh", 
             "protected": False, 
             "default_profile": True, 
             "is_translator": False
           }, 
           "geo": None, 
           "in_reply_to_user_id_str": None, 
           "possibly_sensitive": False, 
           "lang": "en", 
           "created_at": "Sun Oct 26 07:37:55 +0000 2014", 
           "in_reply_to_status_id_str": None, 
           "place": None, 
           "metadata": {
             "iso_language_code": "en", 
             "result_type": "recent"
           }
         }, 
         "user": {
           "follow_request_sent": False, 
           "profile_use_background_image": True, 
           "profile_text_color": "2A48AE", 
           "default_profile_image": False, 
           "id": 104940733, 
           "profile_background_image_url_https": "https://abs.twimg.com/images/themes/theme17/bg.gif", 
           "verified": False, 
           "profile_location": None, 
           "profile_image_url_https": "https://pbs.twimg.com/profile_images/2878477539/78e20432088b5ee2addc9ce3362fd461_normal.jpeg", 
           "profile_sidebar_fill_color": "6378B1", 
           "entities": {
             "description": {
               "urls": []
             }
           }, 
           "followers_count": 149, 
           "profile_sidebar_border_color": "FBD0C9", 
           "id_str": "104940733", 
           "profile_background_color": "0C003D", 
           "listed_count": 18, 
           "is_translation_enabled": False, 
           "utc_offset": 0, 
           "statuses_count": 16031, 
           "description": "Have you any dreams you'd like to sell?", 
           "friends_count": 248, 
           "location": "", 
           "profile_link_color": "0F1B7C", 
           "profile_image_url": "http://pbs.twimg.com/profile_images/2878477539/78e20432088b5ee2addc9ce3362fd461_normal.jpeg", 
           "following": False, 
           "geo_enabled": False, 
           "profile_banner_url": "https://pbs.twimg.com/profile_banners/104940733/1410032966", 
           "profile_background_image_url": "http://abs.twimg.com/images/themes/theme17/bg.gif", 
           "name": "Heather", 
           "lang": "en", 
           "profile_background_tile": False, 
           "favourites_count": 777, 
           "screen_name": "froyoho", 
           "notifications": False, 
           "url": None, 
           "created_at": "Thu Jan 14 21:37:54 +0000 2010", 
           "contributors_enabled": False, 
           "time_zone": "London", 
           "protected": False, 
           "default_profile": False, 
           "is_translator": False
         }, 
         "geo": None, 
         "in_reply_to_user_id_str": None, 
         "possibly_sensitive": False, 
         "lang": "en", 
         "created_at": "Sun Nov 23 20:55:57 +0000 2014", 
         "in_reply_to_status_id_str": None, 
         "place": None, 
         "metadata": {
           "iso_language_code": "en", 
           "result_type": "recent"
         }
       }, 
       {
         "contributors": None, 
         "truncated": False, 
         "text": "RT @NotableHistory: Madonna, 18 year old freshman at the University of Michigan, 1976 http://t.co/x2dm1G67ea", 
         "in_reply_to_status_id": None, 
         "id": 536623674942439425, 
         "favorite_count": 0, 
         "source": "<a href=\"http://twitter.com/download/android\" rel=\"nofollow\">Twitter for Android</a>", 
         "retweeted": False, 
         "coordinates": None, 
         "entities": {
           "symbols": [], 
           "user_mentions": [
             {
               "id": 844766941, 
               "indices": [
                 3, 
                 18
               ], 
               "id_str": "844766941", 
               "screen_name": "NotableHistory", 
               "name": "OnThisDay & Facts"
             }
           ], 
           "hashtags": [], 
           "urls": [], 
           "media": [
             {
               "source_status_id_str": "536610190334779392", 
               "expanded_url": "http://twitter.com/NotableHistory/status/536610190334779392/photo/1", 
               "display_url": "pic.twitter.com/x2dm1G67ea", 
               "url": "http://t.co/x2dm1G67ea", 
               "media_url_https": "https://pbs.twimg.com/media/B3EXbQkCMAEipwM.jpg", 
               "source_status_id": 536610190334779392, 
               "id_str": "536235587703812097", 
               "sizes": {
                 "small": {
                   "h": 487, 
                   "resize": "fit", 
                   "w": 340
                 }, 
                 "large": {
                   "h": 918, 
                   "resize": "fit", 
                   "w": 640
                 }, 
                 "medium": {
                   "h": 860, 
                   "resize": "fit", 
                   "w": 600
                 }, 
                 "thumb": {
                   "h": 150, 
                   "resize": "crop", 
                   "w": 150
                 }
               }, 
               "indices": [
                 86, 
                 108
               ], 
               "type": "photo", 
               "id": 536235587703812097, 
               "media_url": "http://pbs.twimg.com/media/B3EXbQkCMAEipwM.jpg"
             }
           ]
         }, 
         "in_reply_to_screen_name": None, 
         "in_reply_to_user_id": None, 
         "retweet_count": 9, 
         "id_str": "536623674942439425", 
         "favorited": False, 
         "retweeted_status": {
           "contributors": None, 
           "truncated": False, 
           "text": "Madonna, 18 year old freshman at the University of Michigan, 1976 http://t.co/x2dm1G67ea", 
           "in_reply_to_status_id": None, 
           "id": 536610190334779392, 
           "favorite_count": 13, 
           "source": "<a href=\"https://ads.twitter.com\" rel=\"nofollow\">Twitter Ads</a>", 
           "retweeted": False, 
           "coordinates": None, 
           "entities": {
             "symbols": [], 
             "user_mentions": [], 
             "hashtags": [], 
             "urls": [], 
             "media": [
               {
                 "expanded_url": "http://twitter.com/NotableHistory/status/536610190334779392/photo/1", 
                 "display_url": "pic.twitter.com/x2dm1G67ea", 
                 "url": "http://t.co/x2dm1G67ea", 
                 "media_url_https": "https://pbs.twimg.com/media/B3EXbQkCMAEipwM.jpg", 
                 "id_str": "536235587703812097", 
                 "sizes": {
                   "small": {
                     "h": 487, 
                     "resize": "fit", 
                     "w": 340
                   }, 
                   "large": {
                     "h": 918, 
                     "resize": "fit", 
                     "w": 640
                   }, 
                   "medium": {
                     "h": 860, 
                     "resize": "fit", 
                     "w": 600
                   }, 
                   "thumb": {
                     "h": 150, 
                     "resize": "crop", 
                     "w": 150
                   }
                 }, 
                 "indices": [
                   66, 
                   88
                 ], 
                 "type": "photo", 
                 "id": 536235587703812097, 
                 "media_url": "http://pbs.twimg.com/media/B3EXbQkCMAEipwM.jpg"
               }
             ]
           }, 
           "in_reply_to_screen_name": None, 
           "in_reply_to_user_id": None, 
           "retweet_count": 9, 
           "id_str": "536610190334779392", 
           "favorited": False, 
           "user": {
             "follow_request_sent": False, 
             "profile_use_background_image": True, 
             "profile_text_color": "333333", 
             "default_profile_image": False, 
             "id": 844766941, 
             "profile_background_image_url_https": "https://pbs.twimg.com/profile_background_images/458461302696837121/rGlGdWsc.png", 
             "verified": False, 
             "profile_location": None, 
             "profile_image_url_https": "https://pbs.twimg.com/profile_images/481243404320251905/gCr1cVP2_normal.png", 
             "profile_sidebar_fill_color": "DDFFCC", 
             "entities": {
               "url": {
                 "urls": [
                   {
                     "url": "http://t.co/9fTPk5A4wh", 
                     "indices": [
                       0, 
                       22
                     ], 
                     "expanded_url": "http://notablefacts.com/", 
                     "display_url": "notablefacts.com"
                   }
                 ]
               }, 
               "description": {
                 "urls": []
               }
             }, 
             "followers_count": 73817, 
             "profile_sidebar_border_color": "FFFFFF", 
             "id_str": "844766941", 
             "profile_background_color": "9AE4E8", 
             "listed_count": 485, 
             "is_translation_enabled": False, 
             "utc_offset": -21600, 
             "statuses_count": 38841, 
             "description": "On This Day in History, Historical Pictures & other Interesting Facts....Historyfollower@gmail.com", 
             "friends_count": 43594, 
             "location": "", 
             "profile_link_color": "0084B4", 
             "profile_image_url": "http://pbs.twimg.com/profile_images/481243404320251905/gCr1cVP2_normal.png", 
             "following": False, 
             "geo_enabled": False, 
             "profile_banner_url": "https://pbs.twimg.com/profile_banners/844766941/1411076349", 
             "profile_background_image_url": "http://pbs.twimg.com/profile_background_images/458461302696837121/rGlGdWsc.png", 
             "name": "OnThisDay & Facts", 
             "lang": "en", 
             "profile_background_tile": True, 
             "favourites_count": 1383, 
             "screen_name": "NotableHistory", 
             "notifications": False, 
             "url": "http://t.co/9fTPk5A4wh", 
             "created_at": "Tue Sep 25 03:08:59 +0000 2012", 
             "contributors_enabled": False, 
             "time_zone": "Central Time (US & Canada)", 
             "protected": False, 
             "default_profile": False, 
             "is_translator": False
           }, 
           "geo": None, 
           "in_reply_to_user_id_str": None, 
           "possibly_sensitive": False, 
           "lang": "en", 
           "created_at": "Sun Nov 23 20:00:13 +0000 2014", 
           "in_reply_to_status_id_str": None, 
           "place": None, 
           "metadata": {
             "iso_language_code": "en", 
             "result_type": "recent"
           }
         }, 
         "user": {
           "follow_request_sent": False, 
           "profile_use_background_image": True, 
           "profile_text_color": "333333", 
           "default_profile_image": False, 
           "id": 818185729, 
           "profile_background_image_url_https": "https://abs.twimg.com/images/themes/theme1/bg.png", 
           "verified": False, 
           "profile_location": None, 
           "profile_image_url_https": "https://pbs.twimg.com/profile_images/486215801498640384/rz9o7LnF_normal.jpeg", 
           "profile_sidebar_fill_color": "DDEEF6", 
           "entities": {
             "description": {
               "urls": []
             }
           }, 
           "followers_count": 302, 
           "profile_sidebar_border_color": "C0DEED", 
           "id_str": "818185729", 
           "profile_background_color": "C0DEED", 
           "listed_count": 0, 
           "is_translation_enabled": False, 
           "utc_offset": None, 
           "statuses_count": 395, 
           "description": "Formerly with California Dept of General Services, now freelancing around the Sacramento area...", 
           "friends_count": 1521, 
           "location": "Citrus Heights, CA", 
           "profile_link_color": "0084B4", 
           "profile_image_url": "http://pbs.twimg.com/profile_images/486215801498640384/rz9o7LnF_normal.jpeg", 
           "following": False, 
           "geo_enabled": True, 
           "profile_banner_url": "https://pbs.twimg.com/profile_banners/818185729/1383764759", 
           "profile_background_image_url": "http://abs.twimg.com/images/themes/theme1/bg.png", 
           "name": "M Duncan", 
           "lang": "en", 
           "profile_background_tile": False, 
           "favourites_count": 6544, 
           "screen_name": "MDuncan95814", 
           "notifications": False, 
           "url": None, 
           "created_at": "Tue Sep 11 21:02:09 +0000 2012", 
           "contributors_enabled": False, 
           "time_zone": None, 
           "protected": False, 
           "default_profile": True, 
           "is_translator": False
         }, 
         "geo": None, 
         "in_reply_to_user_id_str": None, 
         "possibly_sensitive": False, 
         "lang": "en", 
         "created_at": "Sun Nov 23 20:53:48 +0000 2014", 
         "in_reply_to_status_id_str": None, 
         "place": None, 
         "metadata": {
           "iso_language_code": "en", 
           "result_type": "recent"
         }
       }
     ]
   }   


Entender
---------

En cualquier nivel del proceso de extracción, la primera tarea es asegurarse de que comprende el objeto actual que ha sido
extraído. Hay pocas opciones aquí.

1. Imprima todo el objeto. Si es lo suficientemente pequeño, es posible que pueda entender la impresión directamente. Si es un poco más grande, puede que le resulte útil "imprimirlo bonito", con sangría que muestre el nivel de anidamiento de los datos. No tenemos una forma bonita de imprimir en nuestro entorno basado en el navegador en línea, pero si está ejecutando código con un intérprete completo de Python, puede usar la función dumps en el módulo json. Por ejemplo:

.. sourcecode:: python

   import json
   print(json.dumps(res, indent=2))

2. Si imprimir todo el objeto le da algo demasiado difícil de manejar, tiene otras opciones para darle sentido.

   * Cópielo y péguelo en un sitio como https://jsoneditoronline.org/ que le permitirá explorar y colapsar niveles
   * Imprima el tipo del objeto.
   * Si es un diccionario:
      * imprimir las llaves
   * Si es una lista:
      * imprime su longitud
      * imprime el tipo del primer elemento
      * imprima el primer elemento si es de tamaño manejable

.. activecode:: ac300_1_2
   :include: ac300_1_1

   import json
   print(json.dumps(res, indent=2)[:100])
   print("-----------")
   print(type(res))
   print(res.keys())

Extraer
--------

En la fase de extracción, se sumergirá un nivel más en los datos anidados.

1. Si se trata de un diccionario, averigua qué clave tiene el valor que estás buscando y obtén su valor. Por ejemplo: ``res2 = res['status']``

2. Si se trata de una lista, normalmente querrá hacer algo con cada uno de los elementos (por ejemplo, extraer algo de cada uno y acumularlos en una lista). Para eso, querrás un bucle for, como ``for res2 in res``. Durante su fase de exploración, sin embargo, será más fácil depurar las cosas si trabaja con un solo elemento. Un truco para hacerlo es iterar sobre una porción de la lista que contiene solo un elemento. Por ejemplo, `` para res2 en res[:1]``.

.. activecode:: ac300_1_3
   :include: ac300_1_1

   print(type(res))
   print(res.keys())
   res2 = res['statuses']


Repetir
--------

Ahora repetirá los procesos Entender y Extraer en el siguiente nivel.

Nivel 2
^^^^^^^^^

Primero entienda.

.. activecode:: ac300_1_4
   :include: ac300_1_1

   print(type(res))
   print(res.keys())
   res2 = res['statuses']
   print("----Level 2-----")
   print(type(res2)) # it's a list!
   print(len(res2))
      
Es una lista, con tres elementos, por lo que es una buena suposición de que cada elemento representa un tweet.

Ahora extraer. Como es una lista, queremos trabajar con cada elemento, pero para mantener las cosas manejables por ahora, usemos
un truco para solo mirar el primer elemento. Más tarde pasaremos a procesar todos los artículos.

.. activecode:: ac300_1_5
   :include: ac300_1_1

   import json
   print(type(res))
   print(res.keys())
   res2 = res['statuses'] 
   print("----Level 2: a list of tweets-----")
   print(type(res2)) # es una lista!
   print(len(res2))  # parece un elemento que representa cada uno de los tres tweets
   for res3 in res2[:1]:
      print("----Level 3: a tweet----")
      print(json.dumps(res3, indent=2)[:30])

  
Nivel 3
^^^^^^^^

Primero entienda.

.. activecode:: ac300_1_6
   :include: ac300_1_1

   import json
   print(type(res))
   print(res.keys())
   res2 = res['statuses']
   print("----Level 2: a list of tweets-----")
   print(type(res2)) # es una list!
   print(len(res2))  # parece un elemento que representa cada uno de los tres tweets
   for res3 in res2[:1]:
      print("----Level 3: a tweet----")
      print(json.dumps(res3, indent=2)[:30])
      print(type(res3)) # it's a dictionary
      print(res3.keys())

Luego extraer. Saquemos la información sobre quién envió cada uno de los tweets. Probablemente ese sea el valor asociado con
la clave 'usuario'.

.. activecode:: ac300_1_7
   :include: ac300_1_1

   import json
   print(type(res))
   print(res.keys())
   res2 = res['statuses']
   print("----Level 2: a list of tweets-----")
   print(type(res2)) # es una list!
   print(len(res2))  # parece un elemento que representa cada uno de los tres tweets
   for res3 in res2[:1]:
      print("----Level 3: a tweet----")
      print(json.dumps(res3, indent=2)[:30])
      res4 = res3['user']
      
Ahora repita.

Nivel 4
^^^^^^^^

Entienda.

.. activecode:: ac300_1_8
   :include: ac300_1_1

   import json
   print(type(res))
   print(res.keys())
   res2 = res['statuses']
   print("----Level 2: a list of tweets-----")
   print(type(res2)) # es una lista!
   print(len(res2))  # parece un elemento que representa cada uno de los tres tweets
   for res3 in res2[:1]:
      print("----Level 3: a tweet----")
      print(json.dumps(res3, indent=2)[:30])
      res4 = res3['user']
      print("----Level 4: the user who wrote the tweet----")
      print(type(res4)) # it's a dictionary
      print(res4.keys())

Extraer. Imprimamos el nombre de usuario del usuario y cuándo se creó su cuenta.

.. activecode:: ac300_1_9
   :include: ac300_1_1

   import json
   # print(type(res))
   # print(res.keys())
   res2 = res['statuses']
   # print("----Level 2: a list of tweets-----")
   # print(type(res2)) # es una lista!
   # print(len(res2))  # parece un elemento que representa cada uno de los tres tweets
   for res3 in res2[:1]:
      print("----Level 3: a tweet----")
      # print(json.dumps(res3, indent=2)[:30])
      res4 = res3['user']
      print("----Level 4: the user who wrote the tweet----")
      # print(type(res4)) # it's a dictionary
      # print(res4.keys())
      print(res4['screen_name'], res4['created_at'])

Ahora, es posible que deseemos volver a extraerlo para todos los elementos en lugar de solo el primer elemento en res2.

.. activecode:: ac300_1_10
   :include: ac300_1_1

   import json
   # print(type(res))
   # print(res.keys())
   res2 = res['statuses']
   #print("----Level 2: a list of tweets-----")
   #print(type(res2)) # es una lista!
   #print(len(res2))  # parece un elemento que representa cada uno de los tres tweets
   for res3 in res2:
      #print("----Level 3: a tweet----")
      #print(json.dumps(res3, indent=2)[:30])
      res4 = res3['user']
      #print("----Level 4: the user who wrote the tweet----")
      #print(type(res4)) # it's a dictionary
      #print(res4.keys())
      print(res4['screen_name'], res4['created_at'])

Reflexiones
^^^^^^^^^^^

Observe que cada vez que descendemos un nivel en un diccionario, tenemos un [] seleccionando una clave.
Cada vez que miramos dentro de una lista, tendremos un bucle for. Si hay listas en varios niveles, habremos
anidado bucles for.

Una vez que haya descubierto cómo extraer todo lo que desea, *puede* optar por colapsar las cosas con múltiples extracciones
en una sola expresión Por ejemplo, podríamos tener esta versión más corta.

.. activecode:: ac300_1_11
   :include: ac300_1_1

   for res3 in res['statuses']:
       print(res3['user']['screen_name'], res3['user']['created_at'])

Incluso con este código compacto, aún podemos contar cuántos niveles de anidamiento hemos extraído, en este caso cuatro.
res['statuses'] dice que hemos descendido un nivel (en un diccionario). for res3 in... dice que hemos descendido otro
nivel (en una lista). ['user'] está descendiendo un nivel más y ['screen_name'] está descendiendo un nivel más.

 