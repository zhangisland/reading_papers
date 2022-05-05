# 代码结构

---

## Lib-->Encoder-->Codec

---

### EbRateControlProcess.c

---

#### 结构体RateControlContext
```c
typedef struct RateControlContext {
    EbFifo *rate_control_input_tasks_fifo_ptr;  
    EbFifo *rate_control_output_results_fifo_ptr;
    EbFifo *picture_decision_results_output_fifo_ptr;

    RateControlIntervalParamContext **rate_control_param_queue;  // 参数  
} RateControlContext;
```

其中`RateControlIntervalParamContext`的定义：
```c
typedef struct RateControlIntervalParamContext {
    EbDctor  dctor;  
    uint64_t first_poc;  // ??
    uint64_t last_poc;

    // Projected total bits available for a key frame group of frames
    int64_t kf_group_bits;  
    // Error score of frames still to be coded in kf group
    int64_t kf_group_error_left;
    uint8_t end_of_seq_seen;
    int32_t processed_frame_number;
    uint8_t last_i_qp;  // i帧的QP
} RateControlIntervalParamContext;
```

#### EbErrorType rate_control_coded_frames_stats_context_ctor()
```c
coded_frames_stats_entry *entry_ptr, 
uint64_t picture_number
```
获取待编码状态??，picture_number和frame_total_bit_actual<br>

#### static void rate_control_context_dctor()
```c
EbPtr p
``` 
一些赋值操作，释放`rate_control_param_queue`内存空间<br>

#### EbErrorType rate_control_context_ctor()
```c
EbThreadContext *thread_context_ptr,
const EbEncHandle *enc_handle_ptr, 
int me_port_index
```
其中涉及内存分配
```c
EB_MALLOC_2D(context_ptr->rate_control_param_queue, (int32_t)PARALLEL_GOP_MAX_NUMBER, 1);

#define PARALLEL_GOP_MAX_NUMBER 256
```

#### int32_t svt_av1_convert_qindex_to_q_fp8()
```c
int32_t qindex, 
AomBitDepth bit_depth
```
convert the index to a real Q value(scaled down to match old Q values)<br>

大概是根据色深进行对应的量化??

#### static int get_active_quality()
```c
int q,
int gfu_boost, 
int low, 
int high, 
int *low_motion_minq,
int *high_motion_minq
```

```
IF gfu_boost > high:
THEN low_motion_minq[q]
ELSE IF gfu_boost < low:
THEN high_motion_minq[q]
ELSE:
    普通赋值操作
```



### 常量
#### KeyFrame_threshold
```c
// that are not marked as coded with 0,0 motion in the first pass.
#define FAST_MOVING_KF_GROUP_THRESH 5
#define MEDIUM_MOVING_KF_GROUP_THRESH 30
```





#### 暂时不知
```C
static const double tpl_hl_islice_div_factor[EB_MAX_TEMPORAL_LAYERS]     = {1, 1, 1, 2, 1, 0.7};
static const double tpl_hl_base_frame_div_factor[EB_MAX_TEMPORAL_LAYERS] = {1, 1, 1, 3, 1, 0.9};
#define KB 400

#define MAX_Q_INDEX 255
#define MIN_Q_INDEX 0

#define STATIC_MOTION_THRESH 95  // ??

// that are not marked as coded with 0,0 motion in the first pass.
#define FAST_MOVING_KF_GROUP_THRESH 5
#define MEDIUM_MOVING_KF_GROUP_THRESH 30
#define MAX_QPS_COMP_I 150
#define MAX_QPS_COMP_I_LR 42
#define MAX_QPS_COMP_NONI 300
#define HIGH_QPS_COMP_THRESHOLD 80
#define LOW_QPS_COMP_THRESHOLD 40
#define HIGH_FILTERED_THRESHOLD (4 << 8) // 8 bit precision
#define LOW_FILTERED_THRESHOLD (2 << 8) // 8 bit precision
#define MAX_REF_AREA_I 50 // Max ref area for I slice
#define MAX_REF_AREA_NONI 50 // Max ref area for Non I slice
#define MAX_REF_AREA_NONI_LOW_RES 40 // Max ref area for Non I slice in low resolution
#define REF_AREA_DIF_THRESHOLD 10 // Difference threshold for ref area between two frames
#define REF_AREA_LOW_THRESHOLD 8 // Low threshold for ref area
#define REF_AREA_MED_THRESHOLD 16 // Medium threshold for ref area
#define ME_SAD_LOW_THRESHOLD1 15 // Low sad_ threshold1 for me distortion (very low)
#define ME_SAD_LOW_THRESHOLD2 25 // Low sad_ threshold2 for me distortion (low)
#define ME_SAD_HIGH_THRESHOLD 80 // High sad_ threshold2 for me distortion (high)

static int gf_high_tpl_la = 2400;
static int gf_low_tpl_la  = 300;
static int kf_high        = 5000;
static int kf_low         = 400;

```

# Question

