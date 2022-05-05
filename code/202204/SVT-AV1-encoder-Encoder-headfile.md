# 代码结构

---

## Lib-->Encoder-->Codec

---

### Encoder.h

---

#### Rate control mode
```C
// aom_codec.h
/*!\brief Rate control mode */
enum aom_rc_mode {
    AOM_VBR, /**< Variable Bit Rate (VBR) mode */
    AOM_CBR, /**< Constant Bit Rate (CBR) mode */
    AOM_CQ, /**< Constrained Quality (CQ)  mode */
    AOM_Q, /**< Constant Quality (Q) mode */
};
```

#### SwitchFrameCfg
```C
typedef struct SwitchFrameCfg {
    // Indicates the number of frames after which a frame may be coded as an S-Frame.
    int32_t sframe_dist;
    // 1: the considered frame will be made into an S-Frame only if it is an altref frame.
    // 2: the next altref frame will be made into an S-Frame.
    EbSFrameMode sframe_mode;
} SwitchFrameCfg;
```
alt-ref frame是不可见的，S-frame 应该是skip？即如果当前帧变化不大，就可以把它归到alt-ref frame。<br>


### 常量
#### scenecut
```C
#define SCENE_CUT_KEY_TEST_INTERVAL 16


```

### 定义
#### Frame Type
```C
#define FRAME_TYPE int
```


# Question

