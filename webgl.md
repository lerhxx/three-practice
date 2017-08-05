## 着色器获取数据方式

Vertex shaders

* Attributes: 从 buffers 中获取数据
* Uniforms: 每次绘制中保持不变的数据
* Textures: pixels/texels 的数据

Fragment shaders

* Uniforms: 每次绘制中保持不变的数据
* Textures: pixels/texels 的数据
* Varying: 从 vertex shader 传递用于插补的数据

## 初始化

1. 创建 vertex shader、fragment shader
2. createShader           将 shader source 编译为 shader
3. getShaderParameter     判断 shader 是否创建成功
4. createProgram          创建 shader program
5. attachShader           将 shader 关联到 shader program
6. linkProgram            链接 shader program
7. getProgramParameter    判断 shader program 是否创建成功
8. getAttribLocation           获取 attribute、uniform 位置
9. createBuffer                创建 buffer，分配内存空间
10. bindBuffer                  将 buffer 关联到 bind point
11. bufferData                  将 data 复制到 buffer 中，并告诉 WebGL 如何使用 data

不变的数据都可以在初始化的时候完成

## 渲染

1. viewport                    resize canvas
2. clear                       清除 canvas
3. useProgram                  指定使用的 program
4. enableVertexAttribArray     开启 attribute
5. vertexAttribPointer         将当前 buffer 绑定到指定 attribute 上，告诉 WebGL 如何从 buffer 中获取数据到 attribute 中
6. drawArrays

uniform[1-4][fi][v]()          指定 uniform 变量的值


## webgl 坐标

* x轴 -1 to +1
* y轴 -1 to +1

## 纹理

```
	let tex = gl.createTexture();
	gl.bindTexture(gl.TEXTURE_2D, tex);

	let level = 0,
		width = 2,
		height = 1,
		data = new Unit8Array([
			255, 0, 0, 255,
			0, 255, 0, 255,
		])
	gl.texImage2D(gl.TEXTURE_2D, level, width, height, 0, gl.RGBA, gl.UNSIGNED_BYTE, data);
```

