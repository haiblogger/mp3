# Temaplate Blogger mp3

Demo: https://truyenmahot.com/

Code to post audio

<blockquote><b>Truyện Ma Audio Đình Soạn Oán Nghiệt Quỷ Nhi </b><br/>
Tác giả: <b>Lê Văn Chiến</b><br/>
Giọng đọc: <b>MC Đình Soạn</b><br/>
Thể loại: <b>Chuyện Ma Pháp Sư</b><br/>
Trạng thái: <b>Đã Hoàn Thành</b></blockquote><br/>  <!--more--> 

                         <div class="zingplayer">
                                            <script type="text/javascript">
                                                $(document).ready(function() {
                                                    var cookiezingspeed = $.cookie("zingspeed");
                                                    if (cookiezingspeed == "") {
                                                        cookiezingspeed = 1.1;
                                                    }
                                                    var myPlayer = new jPlayerPlaylist({
                                                        jPlayer: "#zingaudioplayer",
                                                        cssSelectorAncestor: "#zingaudio_container"
                                                    }, [{
                                                       title: " Oán Nghiệt Quỷ Nhi - Tập 1 ",
                                                                 mp3: "https://docs.google.com/uc?id=1sRwnoGWxFl5LUM-juYtXkO_j-LCWYPu7",
                                                            }

                                                ,                 
                                                        {
                                                       title: " Oán Nghiệt Quỷ Nhi - Tập 2 ",
                                                                 mp3: "https://docs.google.com/uc?id=1nYRFlo3MrEk_Hd_rll_XRXlXlEp4YYqS",
                                                            }

                                                ,                 
													{
                                                       title: " Oán Nghiệt Quỷ Nhi - Tập 3 ",
                                                                 mp3: "https://docs.google.com/uc?id=1-j-RyEx1pMgQiUXASTwPddYL9rf5ixCH",
                                                            }

                                                ,                 
 ], {
                                                        swfPath: "/jplayer",
                                                        supplied: "oga, mp3",
                                                        wmode: "window",
                                                        useStateClassSkin: true,
                                                        autoBlur: false,
                                                        smoothPlayBar: true,
                                                        keyEnabled: true,
                                                        defaultPlaybackRate: cookiezingspeed,
                                                        play: function(e) {
                                                            var part = myPlayer.current;
                                                            setCookie_zingaudionew(part);
                                                        },
                                                        timeFormat: {
                                                            showHour: true
                                                        }
                                                    });
                                                    $("#nghetiep").click(function() {
                                                        var dangnghe_part = $.cookie("dangnghe_chuong_new");
                                                        var dangnghe_time = $.cookie("dangnghe_time_new");
                                                        var dangngheInt = parseInt(dangnghe_time);
                                                        dangnghe_part = parseInt(dangnghe_part);
                                                        myPlayer.play(dangnghe_part);
                                                        if (dangngheInt > 0) $("#zingaudioplayer").jPlayer("play", parseInt(dangnghe_time, 10));
                                                        $(".jp-playlist").scrollTop($(".jp-playlist").scrollTop() + $(".jp-playlist-current").position().top - 720);
                                                        $('#nghetiep').hide();
                                                    });

                                                    function setCookie_zingaudionew(part) {
                                                        setTimeout(setCookie_zingaudionew, 10000);
                                                        var currTime = Math.round($("#zingaudioplayer").data("jPlayer").status.currentTime);
                                                        if (currTime === "0:00") {
                                                            var currTime = "undefined";
                                                        }
                                                        $.cookie("dangnghe_chuong_new", part, {
                                                            expires: 365,
                                                            path: window.location.pathname
                                                        });
                                                        $.cookie("dangnghe_time_new", currTime, {
                                                            expires: 365,
                                                            path: window.location.pathname
                                                        });
                                                        var dangnghe_part = $.cookie("dangnghe_chuong_new");
                                                        dangnghe_part++;
                                                        if (currTime > 0 && typeof(currTime) !== "undefined") {
                                                            var textdangNghe = "Đã lưu thời gian đang nghe <b>" + secondsTimeSpanToHMS(currTime) + "</b>.";
                                                            if (dangnghe_part > 1) var textdangNghe = "Đã lưu thời gian đang nghe <b>Tập: " + dangnghe_part + "</b> - <b>Thời gian: " + secondsTimeSpanToHMS(currTime) + "</b>.";
                                                            $("div.showlisten").css("display", "block");
                                                            $('div.showlisten').html(textdangNghe);
                                                        }
                                                    }
                                                    getcookielisten_new();

                                                    function getcookielisten_new() {
                                                        var dangnghe_part = $.cookie("dangnghe_chuong_new");
                                                        var dangnghe_time = $.cookie("dangnghe_time_new");
                                                        dangnghe_part = parseInt(dangnghe_part) + 1;
                                                        var textdangNghe = "Bạn đang nghe đến <b>" + secondsTimeSpanToHMS(dangnghe_time) + "</b>.";
                                                        if (dangnghe_part > 1) var textdangNghe = "Bạn đang nghe đến <b>Tập: " + dangnghe_part + "</b> - <b>Thời gian: " + secondsTimeSpanToHMS(dangnghe_time) + "</b>.";
                                                        if (typeof(dangnghe_time) !== "undefined") {
                                                            $("#nghetiep").css("display", "inline-block");
                                                            $("div.showlisten").css("display", "block");
                                                            $('div.dangnghe').html(textdangNghe);
                                                        }
                                                    }

                                                    function setCookieListAudio() {
                                                        var listaudio_id = $.cookie("listaudio_id");
                                                        if (typeof listaudio_id === "undefined") var listaudio_id = "-2392-";
                                                        else listaudio_id += "2392-";
                                                        $('div.listaudio').html(listaudio_id);
                                                        $.cookie("listaudio_id", listaudio_id, {
                                                            expires: 365,
                                                            path: "/"
                                                        });
                                                    }

                                                    function secondsTimeSpanToHMS(s) {
                                                        var h = Math.floor(s / 3600);
                                                        s -= h * 3600;
                                                        var m = Math.floor(s / 60);
                                                        s -= m * 60;
                                                        return h + ":" + (m < 10 ? '0' + m : m) + ":" + (s < 10 ? '0' + s : s);
                                                    }
                                                });
                                        var currentSpeedIdx = 1;var speeds = [1, 1.1, 1.2, 1.3, 1.4, 1.5, 1.7, 2, 0.5, 0.7, 0.8, 0.9];function jpSpeedControl() {currentSpeedIdx = currentSpeedIdx + 1 < speeds.length ? currentSpeedIdx + 1 : 0;jQuery("#zingaudioplayer").jPlayer("option", "playbackRate", speeds[currentSpeedIdx]);var strInfoSpeed = " (Bình thường)";if (speeds[currentSpeedIdx] == 1.1)
											strInfoSpeed = " (Hơi hơi nhanh)";else if (speeds[currentSpeedIdx] == 1.2)
											strInfoSpeed = " (Hơi nhanh)";else if (speeds[currentSpeedIdx] == 1.3)
											strInfoSpeed = " (Khá nhanh)";else if (speeds[currentSpeedIdx] == 1.4)
											strInfoSpeed = " (Tương đối nhanh)";else if (speeds[currentSpeedIdx] == 1.5)
											strInfoSpeed = " (Nhanh quá)";else if (speeds[currentSpeedIdx] == 1.6)
											strInfoSpeed = " (Rất nhanh)";else if (speeds[currentSpeedIdx] == 1.7)
											strInfoSpeed = " (Siêu nhanh)";else if (speeds[currentSpeedIdx] == 2)
											strInfoSpeed = " (Quá nhanh)";else if (speeds[currentSpeedIdx] == 0.9)
											strInfoSpeed = " (Hơi chậm)";else if (speeds[currentSpeedIdx] == 0.8)
											strInfoSpeed = " (Chậm)";else if (speeds[currentSpeedIdx] == 0.7)
											strInfoSpeed = " (Rất chậm)";else if (speeds[currentSpeedIdx] == 0.5)
											strInfoSpeed = " (Cực kỳ chậm)";else if (speeds[currentSpeedIdx] == 0.5)
											strInfoSpeed = " (Cực kỳ chậm)";jQuery("#jpSpeedControl").val('Tốc độ phát ' + speeds[currentSpeedIdx] + 'x' + strInfoSpeed);}
                                      function zingtua(time) {
                                                    var currTime = Math.round($("#zingaudioplayer").data("jPlayer").status.currentTime);
                                                    var dangngheInt = parseInt(currTime);
                                                    time = time + dangngheInt;
                                                    if (dangngheInt > 0) {
                                                        $("#zingaudioplayer").jPlayer("play", time);
                                                    }
                                                }
                                            </script>
                                       <div id="zingaudioplayer" class="jp-jplayer"></div>
                                            <div id="zingaudio_container" class="jp-audio" role="application" aria-label="media player">
                                                <div class="jp-type-playlist">
                                                    <div class="jp-gui jp-interface">
                                                        <div class="jp-controls">
                                                            <button class="jp-previous fa fa-backward" role="button" tabindex="0"></button>
                                                            <button class="jp-play fa fa-play" role="button" tabindex="0"></button>
                                                            <button class="jp-next fa fa-forward" role="button" tabindex="0"></button>
                                                        </div>
                                                        <div class="jp-progress">
                                                            <div class="jp-seek-bar">
                                                                <div class="jp-play-bar"></div>
                                                            </div>
                                                        </div>
                                                        <div class="jp-time-holder">
                                                            <div class="jp-current-time" role="timer" aria-label="time">&nbsp;</div>
                                                            <div class="jp-duration" role="timer" aria-label="duration">&nbsp;</div>
                                                        </div>
                                                    </div>
                                                    <div class="jp-playlist">
                                                        <ul>
                                                            <li>&nbsp;</li>
                                                        </ul>
                                                    </div>
                                                </div>
                                            </div>
                          					 <div class="zingtua">
												<button type="button" onclick="zingtua(-120)" class="btn btn-default btn-sm">-2m</button>
                                                <button type="button" onclick="zingtua(-60)" class="btn btn-default btn-sm">-1m</button>
                                                <button type="button" onclick="zingtua(-30)" class="btn btn-default btn-sm">-30s</button>
                                                <button type="button" onclick="zingtua(-10)" class="btn btn-default btn-sm">-10s</button>
                                                <button type="button" onclick="zingtua(10)" class="btn btn-default btn-sm">+10s</button>
                                                <button type="button" onclick="zingtua(30)" class="btn btn-default btn-sm">+30s</button>
                                                <button type="button" onclick="zingtua(60)" class="btn btn-default btn-sm">+1m</button>
                                                <button type="button" onclick="zingtua(120)" class="btn btn-default btn-sm">+2m</button>
												<button type="button" onclick="zingtua(300)" class="btn btn-default btn-sm">+5m</button>
                                                <input class="btn btn-default btn-sm" id="jpSpeedControl" type="button" onclick="jpSpeedControl();" value="Tốc độ phát 1x" />
                                            </div>   
                                            <div style="display:none;" class="alert alert-success showlisten">
                                                <button type="button" class="close" data-dismiss="alert">×</button>
                                                <div class="dangnghe"> </div> <a class="btn btn-default" id="nghetiep" href="javascript:;" style="display: none">Nghe tiếp</a>
                                            </div> </div><br/>
											
<h3> GIỚI THIỆU TRUYỆN </h3>


<br/>

truyện ma,truyện ma có thật,truyện ma mới nhất,truyện ma hay,truyện ma mới,quàng a tũn,truyện ma quàng a tũn,quang a tun,đọc truyện đêm khuya,truyện ma làng quê,truyen ma,truyện đêm khuya quàng a tũn,truyện ma đêm khuya,#qat,truyện ma có thật mới nhất,truyện ma đình soạn,đất đồng radio,pháp sư đen,pháp sư tí,cậu tẩy,đồ đệ diêm vương,truyện ma pháp sư diệt quỷ											
