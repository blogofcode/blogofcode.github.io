---
layout:     post
title:      HTTP GET and POST request
date:       2016-11-01 12:31:19
summary:    HTTP request for downloading content from the server and uploading data to the server.
categories: jekyll pixyll
author:     A SAI RAHUL
permalink:  /http-post-and-get-request/
tags:
  - ios-tag
---

In this small blog post, we are going to see how to create and send HTTP GET and POST request with two reuest parameters.

### SETTING UP PROJECT

By default, your app cannot connect to insecure (i.e. HTTP) URL and get data. It's a feature called App Transport Security. You need to make an exception in your app's Info.plist file to connect to HTTP sites.

First, we need to add the NSAppTransportSecurity key inside the Info.plist. This will allow the app to communicate with the servers to get the data. This is not unique to this tutorial. Familiarize yourself with this step, you will be normally using it in the future.

Open the Info.plist and add row. Type in `NSAppTransportSecurity` and press enter to register it. Once it has been added to your list, select add row. Then type in `NSAllowsArbitraryLoads` and set the value to YES.  The following screenshot illustrates what needs to be done.

![desk](https://rawgit.com/blogofcode/blogofcode.github.io/master/images/http-post-and-get-request/Swift-tutorial.png)

### HTTP GET REQUEST

In this tutorial, we are using `URLSession` to get data from the server.

{% highlight swift %}
    let url = URL(string: "URL_STRING")

    let task = URLSession.shared().dataTask(with: url!) { data, response, error in
        guard error == nil else {
            print(error)
            return
        }
        guard let data = data else {
            print("Data is empty")
            return
        }

        let responseString = String(data: data, encoding: .utf8)
        print("responseString = \(responseString)")
    }

    task.resume()
{% endhighlight %}

### HTTP POST REQUEST

This method is to upload data to server.
Here also, we use `URLSession` but pass 2 parameters as string.

{% highlight swift %}
    var request = URLRequest(url: URL(string: "URL_STRING")!)
    request.httpMethod = "POST"
    let postString = "phone=9848022338&name=JACK"
    request.httpBody = postString.data(using: .utf8)
    let task = URLSession.shared.dataTask(with: request) { data, response, error in
        guard let data = data, error == nil else {                                                 
        // check for fundamental networking error
            print("error=\(error)")
            return
        }
        
        if let httpStatus = response as? HTTPURLResponse, httpStatus.statusCode != 200 {           
            // check for http errors
            print("statusCode should be 200, but is \(httpStatus.statusCode)")
        }
        
        let responseString = String(data: data, encoding: .utf8)
        print("responseString = \(responseString)")

    }
    task.resume()
{% endhighlight %}

And there you have it! A simple way to make an HTTP GET and POST request in Swift 3. Now, while we only wrote a few lines of code, you might be unfamiliar with a lot of the terminology used in this post. Fret not! If you want to learn all this things, just search them and learn. But if you want to use just in our app, I suggest just copy the code.

Happy coding!


---