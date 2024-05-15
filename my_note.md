## use
export PYGLET_SHADOW_WINDOW=0
python UVR.py



## translator
```
通用：
选择处理方法：
虚拟现实构架 - 这个模型使用巨型频谱来分离源文件。
MDX-Net - 这个模型混合使用频谱/波形来分离源文件。
demucs V3 - 这个模型混合使用频谱/波形来分离源文件。
组团模式 - 在这里，你能通过多种模型和网络获得最佳的结果。

每种处理方法都有各自的模型及选项，可以在这里选择某种处理方法所关联的模型。
VR 框架 ：
Windows Size - 越小的取样窗将获得越好的转换效果。但是更耗时耗资源。
Aggression（击毁主唱）setting - 设置移除主唱的强度。越高的值提供越深层的抽取。
超过10，将会从“无主唱模型”中得到混响效果的伴奏。
TTA - test-time-augmentation - 增强测试次数/时间，以更长的转换时长为代价提高分离清晰度。
post-process - 后处理。 可能从人声音轨中发现残余的伴奏伪影，此选项可以提升分离度。
此项会起反作用，因为它由音轨质量决定，此项仅建议作为最后的选择进行使用。

1_HP-UVR 给力的器乐曲模型
2_HP-UVR 精调的 1_HP-UVR
3_HP-Vocal-UVR 强调人声提取，主声清晰但音乐浑浊。
4_HP-Vocal-UVR 微加强的 3_HP-Vocal-UVR
5_HP-Karokee-UVR 完好保留伴唱声 ---（不要选中Demucs Model）
6_HP-Karokee-UVR 另一种 5_HP-Karokee-UVR ---（不要选中Demucs Model）
7_HP2-UVR 使用众多数据与参数训练过的 1_HP-UVR
8_HP2-UVR 另一种 1_HP-UVR
9_HP2-UVR 精调的 8_HP2-UVR
MDX-Net：
Chunks - 数据块 ， 允许用户调节内存/显存使用量。
噪声消除 - 用来消除或减弱模型产生的噪音，默认3。
Demucs模型 - 使音轨通过Demucs模型 ，附加进MDX-Net模型来提高分离度。（格外耗时耗资源）
Save Noisy Output - 保存一个附加的未使用噪声消除的声部（声轨的集合）。

UVR-MDX-NET Main - 最强的模型而占用资源也最高。
UVR-MDX-NET 1 - 此模型达到音频质量客观评价指标9.703
UVR-MDX-NET 2 - 此模型达到音频质量客观评价指标9.682
UVR-MDX-NET 3 - 此模型达到音频质量客观评价指标9.662
UVR-MDX-NET Karaoke - 此模型同时也保留伴唱
Demucs V3：
选择声部Stem - 全部 / 人声 / 其他 / 贝斯 / 鼓
segments - 分段（同@数据块），内存/显存占用量
shifts - 执行随机变换多预测平均算法（无GPU就不要选中）
Overlaps - 预测窗口（这个窗口可以参照成语“窥斑见豹”中所使用的工具进行理解）间的重叠区域数值（每个窗口10秒）

Stem Only - 仅保存选择的声部
Mix Without “Stem Only ” - 保存“选择的声部”之外的混合音
Split Mode - 使用Demucs V3的原始方法，并自动禁用“数据块”选项。

（2声部模型）：UVR_Demucs_Model_1 - 由UVR 数据集训练的模型。它仅能提取2个声部，人声 or 其他将被保存
UVR_Demucs_Model_2 - 另一种 UVR_Demucs_Model_1
UVR_Demucs_Model_Bag - 1+2打包
（4声部模型）：mdx_extra - 原始的Demucs小组训练的模型
mdx_extra_q - 量子化的原始的Demucs小组训练的模型，节省资源。
Ensemble组团模式：使用多种模型，合并出富有活力的音频。

Multi-AI Ensemble ： 可以制定多达6名组团成员（默认 UVR_MDX-Net_1 和 2_HP-UVR）

Basic VR Ensemble ： 可以制定多达5名组团成员（默认 1_HP-UVR 和 2_HP-UVR）

Basic MD Ensemble ： 可以制定多达5名组团成员（限MDX-Net和/或Demucs模型）（默认 UVR_MDX-Main 和 UVR_MDX-Net_1）

Manual Ensemble ： 选择2个或以上的团队输出品，人工手动进行分析合成。

Save All Outputs ： 保存每个成员的独立输出。
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Manual Ensemble ：
选择2个或以上的团队输出品，人工手动进行分析合成。
选择算法 algorithm ： Instrumentals（Min Spec）乐曲（最小标准）---加载频谱并预测最小标准值，
Vocals（Max Spec）人声（最大标准）---加载频谱并预测最大标准值
```