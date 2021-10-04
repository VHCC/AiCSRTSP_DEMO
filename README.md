# RTSP_DEMO

SenseTime SDK please Refer Setting-GuideLine by SenseTime

File Tree
```
app > libs > copy "advrtspdemosdk.aar", "insight_sdk_v2.2.0.aar"
```

@build.gradle
```
android {
  repositories {
        flatDir {
            dirs 'libs'
        }
    }
}

dependencies {
...
  implementation(name: 'advrtspdemosdk', ext: 'aar')
  implementation(name: 'insight_sdk_v2.2.0', ext: 'aar')
}
```

In createView
```
TextureView rtspVideo1;
TextureView rtspVideo2;

ImageView imageView1;
ImageView imageView2;
RTSPAgent.getInstance().setRTSP_1_IO(rtspVideo1, imageView1);
RTSPAgent.getInstance().setRTSP_2_IO(rtspVideo2, imageView2);
```

After SenseInsight InitCallBack()
```
new InitCallBack() {
      @Override
      public void success(StDetectService service) {
              RTSPAgent.getInstance().initAgent(getBaseContext(), service, mAgentListener);

              RTSPAgent.getInstance().setRTSPChannel_1_address("rtsp://172.22.24.90:8554/rtsp1");
              playButton1.setOnClickListener(new View.OnClickListener() {
                  @Override
                  public void onClick(View view) {
                      RTSPAgent.getInstance().playRTSPChannel_1();
                  }
              });

              RTSPAgent.getInstance().setRTSPChannel_2_address("rtsp://172.22.24.90:8554/rtsp2");
              playButton2.setOnClickListener(new View.OnClickListener() {
                  @Override
                  public void onClick(View view) {
                      RTSPAgent.getInstance().playRTSPChannel_2();
                  }
              });

  }
```

To Customize Bitmap From callback
```
private RTSPAgent.AgentListener mAgentListener = new RTSPAgent.AgentListener() {
    @Override
    public void onBitmapChannel1(Bitmap bitmapFromChannel_1) {

    }

    @Override
    public void onBitmapChannel2(Bitmap bitmapFromChannel_2) {

    }
};
```
