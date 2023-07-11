<template>
    <body>
        <div id="popup">
            <div id="panel">
                <div class="greeting"></div>
                <div class="triangleUnderGreet"></div>
                <div class="corner"></div>
                <div id="info">
                    <h2 class="user_name" id="uname">{{ uname }}</h2>
                    <div id="info_content">
                        <div class="label_text">已连接<p class="english">Duration</p>
                        </div>
                        <div class="content_text"><span id="clock" style="color:#ec6677">{{ times }}</span>
                            <span class="unit"></span>
                        </div>
                        <div class="label_text">已用流量<p class="english">Usage</p>
                        </div>
                        <div class="usage_bar">
                            <ul class="calibration">
                                <!--As a result of right flow-->
                                <li>125</li>
                                <li>100</li>
                                <li>75</li>
                                <li>50</li>
                            </ul>
                            <div id="usage_value" :style="usage_value"></div>
                            <div class="content_text"><span class="unit" id="usage_flux">{{ usage_flux.toFixed(2) }}G</span>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="disconnectBar">
                    <button class="disconnect"> </button>
                </div>

                <ul id="links">
                    <li><a id="link_info" href="http://info.tsinghua.edu.cn" title="清华信息门户&#10;info.tsinghua">Info</a></li>
                    <li><a id="lib" href="http://lib.tsinghua.edu.cn/" title="清华图书馆&#10;lib.tsinghua">Lib</a></li>
                    <li><a id="learn" href="http://learn.tsinghua.edu.cn/" title="清华网络学堂&#10;learn.tsinghua">Learn</a></li>
                    <li><a id="mail" href="http://mail.tsinghua.edu.cn/" title="清华邮箱&#10;mail.tsinghua">Mail</a></li>
                </ul>
            </div>


        </div>
    </body>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
@Options({
    props: {
        uname: String,
        // times: String,
        // usage_flux: Number,
        // usage_value: String,
    }
})
export default class Popout extends Vue {
    uname!: string;
    times!: string;
    usage_flux = 42.98;
    usage_value = "width: " + String(this.usage_flux / 150.0 * 100.0) + "%;";

    private currentTime: Date = new Date();
    private enterTime: Date = new Date();

    mounted(): void {
        this.updateTime();
        setInterval(this.updateTime, 1000);

        setInterval(() => {
            this.usage_flux += 1;
        }, 1000);

        setInterval(() => {
            this.usage_value = this.get_usage_value;
        }, 1000);
    }

    updateTime() {
        this.currentTime = new Date();
        const duration = this.currentTime.getTime() - this.enterTime.getTime();

        // Convert duration from milliseconds to hours, minutes, and seconds
        const hours = Math.floor(duration / (1000 * 60 * 60));
        const minutes = Math.floor((duration % (1000 * 60 * 60)) / (1000 * 60));
        const seconds = Math.floor((duration % (1000 * 60)) / 1000);

        // Format hours, minutes, and seconds as strings with leading zeros
        const formattedHours = String(hours).padStart(2, '0');
        const formattedMinutes = String(minutes).padStart(2, '0');
        const formattedSeconds = String(seconds).padStart(2, '0');

        // Create the formatted duration string
        this.times = `${formattedHours}:${formattedMinutes}:${formattedSeconds}`;
        console.log(this.times);
    }

    get get_usage_value(): string {
        return `width: ${this.usage_flux / 150.0 * 100.0}%;`;
    }
}
</script>

<style scoped lang="scss">
@import '../assets/css/Popout.scss'
</style>
