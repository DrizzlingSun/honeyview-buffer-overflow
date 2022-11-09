# honeyview-buffer-overflow
Honeyview存在缓冲区溢出漏洞，Honeyview可以无需解压直接查看压缩包（如zip）中的图像，但是当一个畸形的zip文件以不正确的文件后缀名（如bmp、jpg等）读入软件时，会导致crash。
