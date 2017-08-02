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

## GL状态常量(GL State Constants)

### 剔除面(Cull Face)

* THREE.CullFaceNone：多边形面不剔除
* THREE.CullFaceBack：多边形反面剔除
* THREE.CullFaceFront：多边形正面剔除
* THREE.CullFaceFrontBack：多边形正反面都剔除

###正面方向(Front Face Direction)

* THREE.FrontFaceDirectionCW：多边形正面方向：顺时针为0(CW = Clockwise)
* THREE.FrontFaceDirectionCCW: 多边形正面方向：逆时针为1(CCW = Count Clockwise)

## 材料常量(Material Conastants)

### 面(Side)

* Three.FrontSide：前面
* Three.BackSide：后面
* Three.DoubleSide：双面

### 着色方式(Shading)

* THREE.FlatShading：平面着色，也称之为“恒量着色”，非常适用于快速成像以及其他速度要求高于细致度的场合。
* THREE.SmoothShading：平滑着色，用多种颜色进行绘制，每个顶点都是单独进行处理的，各顶点和各图元之间采用均匀插值。

### 颜色(Colors)

将 Geometry 对象转换为 BufferGeometry 对象时，用来设置转换后的对象顶点从哪里继承颜色。

* THREE.NoColors：顶点没有颜色
* THREE.FaceColors：顶点使用面的颜色
* THREE.VertexColors：顶点使用顶点的颜色

### 混合模式(Blending Mode)

定义材料混合模式常量

* THREE.NoBlending：无混合
* THREE.NormalBlending：普通混合
* THREE.AdditiveBlending：加法混合
* THREE.SubtractiveBlending：减法混合
* THREE.MultiplyBlending：乘法混合
* THREE.CustomBlending：自定义混合

### 阴影类型常量(Shadowing Type Constants)
 
 * THREE.BasicShadowMap：普通阴影映射
 * THREE.PCFShadowMap：柔化边缘的阴影映射
 * THREE.PCFSoftShadowMap：柔化边缘的软阴影映射

 ### 纹理常量(Texture Constants)

 #### 运算(Operations)

 * THREE.MultiplyOperation：乘法运算
 * THREE.MixOperation：混合运算
 * THREE.AddOperation：加法运算

 #### 映射模式(Mapping Modes)

 * THREE.UVMapping：最常用的平铺映射
 * THREE.CubeReflectionMappint：立方体反射映射
 * THREE.CubeRefractionMapping：立方体折射映射
 * THREE.EquirectangularReflectionMapping：圆柱反射映射
 * THREE.EquirectangularRefractionMapping：圆柱折射映射
 * THREE.SphericalReflectionMapping：球面反射映射

 #### 包装模式(Wrapping Modes)

 * THREE.RepeatWrapping：平铺重复
 * THREE.ClampToEdgeWrapping：夹边
 * THREE.MirroredRepeatWrapping：镜像重复

 #### 过滤器(Filters)

 * THREE.NearestFilter：最近滤镜。
 * THREE.NearestMipMapNearestFilter：选择最临近的 mip 层，并执行最临近的过滤
 * THREE.NearestMipMapLinearFilter：在 mip 层之间执行线性插补，并执行临近的过滤
 * THREE.LinearFilter：在纹理层上执行线性过滤
 * THREE.LinearMipMapNearestFilter：选择最临近的 mip 层，并执行线性过滤
 * THREE.LinearMipMapLinearFilter：在 mip 层之间执行线性插补，并执行线性过滤

 #### 数据类型(Data Types)

 * THREE.UnsignedByteType：无符号 8 位整型值（1个字节）
 * THREE.ByteType：带符号 8 位整型值（1个字节）
 * THREE.ShortType：带符号 16 位整型值（2个字节）
 * THREE.UnsignedShortType：无符号 16 位整型值（2个字节）
 * THREE.IntType：带符号 32 位整型值（4个字节）
 * THREE.UnsignedIntType：无符号 32 位整型值（4个字节）
 * THREE.FloatType：单精度浮点型（4个字节）
 * THREE.HalfFloatType：半浮点型

 #### 像素类型(Pixel Types)

 * THREE.unsignedShort4444Type：压缩到不带符号 16 位整形：R4,G4,B4,A4
 * THREE.UnsignedShort5551Type：压缩到不带符号 16 位整形：R5,G5,B5,A1
 * THREE.UnsignedShort565Type：压缩到不带符号 16 位整形：R5,G6,B5

 #### 像素格式(Pixel Formats)

 * THREE.AlphaFormat：对应于 GL_ALPHA，Alpha 值
 * THREE.RGBFormat：三原色值
 * THREE.RGBAFormat：rgb 和 alpha 值
 * THREE.LuminanceFormat：灰度值
 * THREE.LuminanceAlphaFormat：灰度值和 Alpha 值
 