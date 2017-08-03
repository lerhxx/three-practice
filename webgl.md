## 初始化

1. 创建 vertex shader、fragment shader
2. createShader           将 shader source 编译为 shader
3. getShaderParameter     判断 shader 是否创建成功
4. createProgram          创建 shader program
5. attachShader           将 shader 关联到 shader program
6. linkProgram            链接 shader program
7. getProgramParameter    判断 shader program 是否创建成功

## 渲染

1. getAttribLocation           获取 attribute、uniform 位置
2. createBuffer                创建 buffer，分配内存空间
3. bindBuffer                  将 buffer 关联到 bind point
4. bufferData                  将 data 复制到 buffer 中，并告诉 WebGL 如何使用 data
5. viewport                    resize canvas
6. clear                       清除 canvas
7. useProgram                  指定使用的 program
8. enableVertexAttribArray     开启 attribute
9. vertexAttribPointer         将当前 buffer 绑定到指定 attribute 上
10. drawArrays


## webgl 坐标

* x轴 -1 to +1
* y轴 -1 to +1