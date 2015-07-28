# Video.js Resolution Switcher

Resolution switcher for [video.js](https://github.com/videojs/video.js) build for [5.0.0-rc.29](https://github.com/videojs/video.js/tree/v5.0.0-rc.29)

## Getting Started

Setup sources dynamically:

```html
<video id='video' class="video-js vjs-default-skin"></video>
<script src="video.js"></script>
<script src="videojs-resolution-switcher.js"></script>
<script>
  videojs('video', {
    controls: true
  }, function(){
  
    // Add dynamically sources via updateSrc method
    player.updateSrc([
        {
          src: 'http://media.xiph.org/mango/tears_of_steel_1080p.webm',
          type: 'video/webm',
          label: '360'
        },
        {
          src: 'http://mirrorblender.top-ix.org/movies/sintel-1024-surround.mp4',
          type: 'video/mp4',
          label: '720'
        }
      ])

      player.on('resolutionchange', function(){
        console.info('Source changed to %s', player.src())
      })
      
  }).videoJsResolutionSwitcher();
</script>
```

Or use `<source>` tags:

```html

<video id="video" class="video-js vjs-default-skin" width="1000" controls data-setup='{}'>
   <source src="http://mirrorblender.top-ix.org/movies/sintel-1024-surround.mp4" type='video/mp4' label='SD' />
   <source src="http://media.xiph.org/mango/tears_of_steel_1080p.webm" type='video/webm' label='HD'/>
</video>
 <script>
  videojs('video').videoJsResolutionSwitcher()
</script>

```

There's also a [working example](example.html) of the plugin you can check out if you're having trouble.

## Methods


### updateSrc([source])

```javascript

// Update video sources
player.updateSrc([
  { type: "video/mp4", src: "http://www.example.com/path/to/video.mp4", label: 'SD' },
  { type: "video/mp4", src: "http://www.example.com/path/to/video.mp4", label: 'HD' },
  { type: "video/mp4", src: "http://www.example.com/path/to/video.mp4", label: '4k' }
])

```
#### PARAMETERS:
 * source `Array` array of sources


## Events

### resolutionchange `EVENT`

> Fired when resolution is changed


