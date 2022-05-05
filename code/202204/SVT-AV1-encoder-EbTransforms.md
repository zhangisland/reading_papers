# 代码结构

---

## Lib-->Encoder-->Codec

---

### EbTransforms.c

---

#### static const int8_t *fwd_txfm_range_mult2_list[TXFM_TYPES]
```C
 = {
    fdct4_range_mult2,
    fdct8_range_mult2,
    fdct16_range_mult2,
    fdct32_range_mult2,
    fdct64_range_mult2,
    fadst4_range_mult2,
    fadst8_range_mult2,
    fadst16_range_mult2,
    fadst32_range_mult2,
    fidtx4_range_mult2,
    fidtx8_range_mult2,
    fidtx16_range_mult2,
    fidtx32_range_mult2,
    fidtx64_range_mult2};
```
tx is abbr. of transformer<br>

定义变换范围??<br>
提供的变换类型：DCT，ADST，IDTX（不变换）。<br>


#### static const int8_t *fwd_txfm_shift_ls[TX_SIZES_ALL]
```C
= {
    fwd_shift_4x4,   fwd_shift_8x8,   fwd_shift_16x16, fwd_shift_32x32, fwd_shift_64x64,
    fwd_shift_4x8,   fwd_shift_8x4,   fwd_shift_8x16,  fwd_shift_16x8,  fwd_shift_16x32,
    fwd_shift_32x16, fwd_shift_32x64, fwd_shift_64x32, fwd_shift_4x16,  fwd_shift_16x4,
    fwd_shift_8x32,  fwd_shift_32x8,  fwd_shift_16x64, fwd_shift_64x16,
};
```
定义变换移位??<br>

#### void svt_av1_gen_fwd_stage_range()
```C
int8_t *stage_range_col, 
int8_t *stage_range_row,
const Txfm2dFlipCfg *cfg,  //config
int32_t bd  // bandwidth?? 
```
为forward stage做准备<br>

#### #define range_check()  ??
```C
#define range_check(stage, input, buf, size, bit) \
    do {                                          \
    } while (0)
```
<br>

#### void svt_av1_fdct4_new()  
```C
const int32_t *input, 
int32_t *output, 
int8_t cos_bit,  // cosine_bit??
const int8_t *stage_range
``` 
对4x4块执行DCT（discrete cosine transform）变换<br>
这是一维变换<br>

类似的还有
```C
void svt_av1_fdct8_new()
void svt_av1_fdct16_new()
void svt_av1_fdct32_new()
void svt_av1_fdct64_new()
```

#### void svt_av1_fadst4_new()
```C
const int32_t *input, 
int32_t *output, 
int8_t cos_bit,
const int8_t *stage_range
```
对4x4块执行ADST变换<br>
这也是一维变换<br>


类似的还有
```C
void svt_av1_fadst8_new()
void svt_av1_fadst16_new()
void av1_fadst32_new()
```
DCT32的stage数目比ADST32的要短。

#### void svt_av1_fidentity4_c()
```C
const int32_t *input, 
int32_t *output, 
int8_t cos_bit,
const int8_t *stage_range
```
对4x4块执行恒等变换，即不进行变换，按像素块数执行下方语句（4x4）<br>

```C
output[i] = round_shift((int64_t)input[i] * new_sqrt2, new_sqrt2_bits);
static const int32_t new_sqrt2 = 5793;
static const int32_t new_sqrt2_bits = 12;
```

类似的还有
```C
void svt_av1_fidentity8_c() :: output[i] = input[i] * 2;
void svt_av1_fidentity16_c() :: output[i] = round_shift((int64_t)input[i] * 2 * new_sqrt2, new_sqrt2_bits);
void svt_av1_fidentity32_c() :: output[i] = input[i] * 4;
void av1_fidentity64_c() :: output[i] = round_shift((int64_t)input[i] * 4 * new_sqrt2, new_sqrt2_bits);
```

#### static INLINE TxfmFunc fwd_txfm_type_to_func(TxfmType txfmtype)
内联函数，根据txfmtype（变换类型）执行对应函数。<br>

#### static INLINE void av1_tranform_two_d_core_c()
```C
int16_t *input, 
uint32_t input_stride, 
int32_t *output,
const Txfm2dFlipCfg *cfg, 
int32_t *buf,
uint8_t bit_depth 
```
关于二维变换<br>

```C
const int32_t txfm_size_col = tx_size_wide[cfg->tx_size];
const int32_t txfm_size_row = tx_size_high[cfg->tx_size];
```
以上，说明执行变换的基本单位其实还是正方形变换。<br>

其中会调用[svt_av1_gen_fwd_stage_range](#void-svt_av1_gen_fwd_stage_range)<br>



--- 

### 常量
#define BETA_P 1  // ??
#define BETA_N 3  // ??

#define ALPHA_0000 0  // ??
#define ALPHA_0050 50
#define ALPHA_0100 100
#define ALPHA_0200 200
#define ALPHA_0300 300
#define ALPHA_0500 500
#define ALPHA_1000 1000




# Question

