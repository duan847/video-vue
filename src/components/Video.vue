<template>
    <div class="test_two_box">
        <video id="myVideo" class="video-js vjs-default-skin vjs-big-play-centered vjs-fluid">
            <source src="https://vs1.baduziyuan.com/20180302/n0p7raJ9/index.m3u8" type="application/x-mpegURL">
        </video>
    </div>
</template>
<script>
    import video from 'video.js'
    import 'video.js/dist/video-js.css'

    /* eslint-disable */
    export default {
        name: "TestTwo",
        data() {
            return {};
        },
        mounted() {
            this.initVideo();
        },
        methods: {
            back(){
                alert(123)
            },
            initVideo() {
                //初始化视频方法
                let myPlayer = video('myVideo', {
                    //确定播放器是否具有用户可以与之交互的控件。没有控件，启动视频播放的唯一方法是使用autoplay属性或通过Player API。
                    controls: true,
                    //自动播放属性,muted:静音播放
                    autoplay: "muted",
                    //建议浏览器是否应在<video>加载元素后立即开始下载视频数据。
                    preload: "auto",
                    //设置视频播放器的显示宽度（以像素为单位）
                    width: "500px",
                    //设置视频播放器的显示高度（以像素为单位）
                    height: "400px",
                    //倍速
                    playbackRates: [0.5, 1, 1.5, 2, 4],
                    responsive:true,
                    userActions: {
                        hotkeys: function(event) {
                            // `this` is the player in this context
                            // `x` key = pause
                            if (event.which === 88) {
                                this.pause();
                            }
                            // `y` key = play
                            if (event.which === 89) {
                                this.play();
                            }
                        }
                    }
                });

                // myPlayer.on('pause', function() {
                //
                //     // Modals are temporary by default. They dispose themselves when they are
                //     // closed; so, we can create a new one each time the player is paused and
                //     // not worry about leaving extra nodes hanging around.
                //     var modal = myPlayer.createModal('This is a modal!');
                //
                //     // When the modal closes, resume playback.
                //     modal.on('modalclose', function() {
                //         player.play();
                //     });
                // });
            }
        }
    };
</script>

<style scoped>
</style>
