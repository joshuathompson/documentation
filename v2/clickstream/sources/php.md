---
title: PHP
sidebar: platform_sidebar
---


## PHP

This library lets you record analytics data from your PHP code. It is a little different than other server-side libraries in that PHP is a single-threaded language, meaning it only processes once language at a time. 

### Getting Started with PHP

#### Step 1

Clone the PHP integration into your application directory.
```
git clone https://github.com/astronomerio/analytics-php
```

#### Step 2

Add the following to your code to load in the library.
```
require_once(\"/path/to/analytics-php/lib/Segment.php\");
```

#### Step 3

Initialize the module with the Source ID found in the setting sections of your Astronomer account. Note that you are only required to do this intitialization once.
```
class_alias('Segment', 'analytics');
analytics::init("ASTRONOMER_APP_ID");
```

After this initialization, you have a ready-to-use instance with all calls built in. 
*Note: We've standardized to analytics.js. If you've used a tool like [Segment](https://segment.com/) in the past, you will find that instrumenting events in Astronomer works in the exact same way.*

### Calls in PHP

Check out our [Calls](../calls.md) section for information on when you should use each call. Below are some examples of how you'd call specific objects in PHP.

#### Identify
```
analytics::identify(array(
         "userId" => "1234qwerty",
         "traits" => array(
         "name" => "Arthur Dent",
         "email" => "earthling1@hitchhikersguide.com\",
         "hasTowel" => True,)
);
```

#### Track
```
analytics::track(array(
        "userId" => "1234qwerty",
        "event" => "Added File",
        "properties" => array(
        "fileTitle" => "Life, the Universe, and Everything\",
        "fileSize" => "42kb",
        "fileType" => "PDF")
        )
);
```

#### Page
```
analytics::page(array(
        "userId" => "1234qwerty",
        "section" => "Blog",
        "name" => "10 Questions with Marvin, the clinically depressed robot",
        "properties" => array(
        "referrer" => "http://reddit.com/r/AMA")
        )
);
```

#### Group
```
analytics::group(array(
        "userId" => "1234qwerty",
        "groupId" => "5678dvorak",
        "traits" => array(
        "name" => "The Hitchhikers",
        "relativePosition" => "[39.1000° N, 84.5167° W]")
        )
);
```

#### Alias
```
analytics::alias(array(
        "previousId" => "1ff049u10459u7",
        "userId" => "1234qwerty")
);
```
