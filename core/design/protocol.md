# 联动服务商API接入文档

![内部调用关系图](C:\Users\renjie\git\OffLineApi\assets\img\trans\queryOrder\innerRela.png)

st=>start: Start:>https://www.zybuluo.com

io=>inputoutput: verification
op=>operation: Your Operation
cond=>condition: Yes or No?
sub=>subroutine: Your Subroutine
e=>end

st->io->op->cond
cond(yes)->e
cond(no)->sub->io

```

```