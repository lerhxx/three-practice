# three-practice

## 剪切测试 scissor test

## 多重采样的片源操作

## 模板测试 stencil test

## 深度测试 depth test

## 融混 blending

### 计算公式

`(RsSr + RdDr, GsSg + GdDg, BsSb + BdDb, AsSa + AdDa)`

颜色分量 [0, 1]

### 混合方程式：

`glBlendEquation(GLenum mode);`

<table>
	<tr>
		<th>
			GLenum mode
		</th>
		<th>
			公式
		</th>
	</tr>
	<tr>
		<td>
			GL_FUNC_ADD
		</td>
		<td>
			Cf = (Cs * S) + (Cd * D)
		</td>
	</tr>
	<tr>
		<td>
			GL_FUNC_SUBTRACT
		</td>
		<td>
			Cf = (Cs * S) - (Cd * D)
		</td>
	</tr>
	<tr>
		<td>
			GL_FUNC_RESERSE_SUBTRACT
		</td>
		<td>
			Cf = (Cd * D) - (Cs * S)
		</td>
	</tr>
	<tr>
		<td>
			GL_MIN
		</td>
		<td>
			Cf = min(Cs, Cd)
		</td>
	</tr>
	<tr>
		<td>
			GL_MAX
		</td>
		<td>
			Cf = max(Cs, Cd)
		</td>
	</tr>
</table>

* Cf 表示混合后的颜色
* Cd 表示混合前颜色缓冲中的颜色值，即目标颜色
* Cs 表示将要绘制的颜色值，即源颜色
* S 为 glBlendFunc 函数设置时的第一个参数，源颜色因子
* D 为 glBlendFunc 函数设置时的第二个参数，目标颜色因子

### 目标因子(Destination Factors)

* THREE.ZeroFactor：GL_ZERO，表示使用0.0作为因子，即该颜色不参与混合运算
* THREE.OneFactor：GL_ONE，表示使用1.0作为因子，即完全使用该颜色参与混合运算
* THREE.SrcColorFactor：GL_SRC_COLOR，表示使用源颜色的四个分量分别作为因子的四个分量
* THREE.OneMinusSrcColorFactor：GL_ONE_MINUS_SRC_COLOR，表示使用1.0减去源颜色的四个分量分别作为因子的四个分量
* THREE.SrcAlphaFactor：GL_SRC_ALPHA，表示使用源颜色的 alpha 值作为因子
* THREE.OneMinusSrcAlphaFactor：GL_ONE_MINUS_SRC_ALPHA，表示使用1.0减去源颜色的alpha值作为因子
* THREE.DstAlphaFactor：GL_DST_ALPHA，表示使用目标颜色的 alpha 值来作为因子
* THREE.OneMinusDstAlphaFactor：GL_ONE_MINUS_DST_ALPHA，表示使用1.0减去目标颜色的 alpha 值作为因子


### 源因子(Source Factors)

* THREE.DstColorFactor：GL_DST_COLOR，表示使用目标颜色的四个分量分别作为因子的四个分量
* THREE.OneMinusDstColorFactor：GL_ONE_MINUS_DST_COLOR，表示使用1.0减去目标颜色的四个分量分别作为因子的四个分量
* THREE.SrcAlphaSaturateFactor：GL_SRC_ALPHA_saturate，表示源颜色的 alpha 值和 RGB 值采用不同的混合因子

## 抖动 dithering

## 逻辑操作 OR，XOR，INVERT