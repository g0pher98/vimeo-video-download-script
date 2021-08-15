# vimeo-video-download-script
Vimeo Player Video Download Script

# Sites using vemo
- swapcard

# Usage
You can run the script below from the `console` tab in the `developer tools(F12)` on a page that only Vimeo Player plays.

``` javascript
var initial_script = top.document.querySelector('body>script').innerHTML;

// regex
var master_link_regex = RegExp('([a-zA-Z0-9-~=:%/\/\.,]+master\.json)');

var master_link = master_link_regex.exec(initial_script)[0];
fetch(master_link).then(r=>r.json()).then(function(resp) {
    var video_id = resp.video.slice(-1)[0].id;

    window.location.href = master_link.replace(/\/sep\/.*/ig, `/parcel/video/${video_id}.mp4`);
})
```

## When it's hard to find a page that only Vimeo Player plays
![image](https://user-images.githubusercontent.com/44149738/129487575-48b80970-4c34-4e00-b490-6392c5d7f9d0.png)  
1. Open the page that contains the video.
2. Open `network` tab in the `Developer tools(F12)`  
3. Input `master.json` into Filter
4. Refresh page(F5)
5. Double click for move `master.json` page
6. Copy URL and back to page that contains the video.
7. Run the script below with change `master_link`  

``` javascript
var master_link = "???" // Replaced the URL you just copied!! 
fetch(master_link).then(r=>r.json()).then(function(resp) {
    var video_id = resp.video.slice(-1)[0].id;

    window.location.href = master_link.replace(/\/sep\/.*/ig, `/parcel/video/${video_id}.mp4`);
})
```

