# Electronic_Design_Competition
2024年全国大学生电子设计竞赛湖南赛区赛暨模拟电子系统设计专题赛初赛——AC-AC变换电路并联运行（A题）

一、前言

今年电赛已经是up第三次参加了，第一年电赛作为大一的小学弟，缺乏项目经验还不是很会，一开始打比赛的目的只是跟着学长学姐学东西。第二年电赛由于是23年国赛，因此指导老师和我们团队都是比较重视，我们花了一年的时间去为国赛做准备。期间我们从最简单的buck开始做起，然后再把基本的电力电子拓扑都做了一遍，包括全桥整流、全桥逆变、三相整流、三相逆变等等，并且做了并网（因为今年我们猜题便是并网方向）。在这期间的训练中，我们积累了很多项目及调试经验，也根据往年赛题，基本上把各个部分的硬件和软件都准备的十分充足。等到赛题一出，如我们猜题的方向一致，23年电赛的题目是单相逆变器并联运行系统并且需要进行并网，这些我们在平时的训练中都做过，唯独没有去做过并联系统，后面在今年的电赛也是栽在了这上面。题目出来后我们讨论的方案是使用dq解耦实现单相逆变器，然后发挥部分的并联系统采用主从控制，使用逆变器2去采集逆变器1的电压电流相位，相当于用逆变器2去并网逆变器1，然后再去进行真正并网。方案确认后我们在第一天晚上就将基础部分全部实现，并且指标十分可观，远超题目要求。然后去做发挥部分时我们便遇到了问题，由于组委会在后面补充说明了两个逆变器之间不能进行有线和无线通讯，因此给我们带来了较大的难题。后面我们放弃了主从控制方案，选择了不需要通讯的下垂控制。由于从来没做过此类方法，因此花了较多的时间去进行理解和实现。在并联时，系统的电流环流会倒灌进直流电源，因此总是会触发短路保护，由于现象有点吓人并且怕损坏电源，因此不怎么敢尝试，中间就一直卡在这一步，到最后一天晚上，我们硬着头皮联调，现象不对随时准备关电。最后在第四天下午也是成功将两个逆变器并联上，虽然效果不是很好，但是也算实现了功能，后面的电流分配和并网便没有多余时间去做了。因此下午便是测试和封箱，由于缺乏比赛经验，比较怕这怕那的，担心测试的时候评委不让手动操作，因此又在逆变器2输出加了一个继电器充当开关，软件延时去控制继电器导通。结果正是这一举动导致前面的努力白费，可能是由于上电时序不对，上电瞬间便把逆变器1给烧了，而且是在封箱之前出的问题，我们也没有多余的时间去解决问题，所以最终只保住了基础部分。最终结果便是基础部分拿满并且指标可观，但是结果还是省二无缘国赛。
  
怀着去年的遗憾我继续参加了今年的电赛，本来都不准备打了，但听说今年专题赛和省赛合并，可能也有机会参加国赛，便拉着队友继续参加，后来才知道这个国赛邀请赛和大多数人都没关系。今年的省赛我的心态比去年要好得多，因为去年带的22级大一队伍学习了一年也有一定的水平了，所以就让他们成为主力。不像去年23年国赛，带着一支大一队伍，所有的压力都是我们队伍抗，并且硬熬四天三夜，今年有队伍和我们分担压力，因此前两天我们都不熬夜，状态比去年好得多。今年的器件清单给了自耦调压器，就在所有人都在准备单相整流时，组委会又给了大家当头一棒。当题目出来的那刻所有人都傻眼了，要求实现一个AC-AC降压变换电路并且要并联，所以之前准备的东西都不大用的上了，只能说组委会出的题目越来越新颖了，在电赛所有的拓扑基本上考完的情况下，电赛题目今后会越来越难。题目要求实现的AC-AC变换电路网上的资料少的可怜，更别说有人做出实物来。我们的指导老师看了题目之后只想到了用矩阵变换器实现，但那个太复杂不太好做，后面问了我们的想法后便按照我们的方案做，后面便没再管过我们了，我估计今年我们老师应该是直接放弃了，但好在我们自己没放弃，最终实现了整个题目要求。今年整个比赛的过程实属不易，主电路硬件和软件都是从无到有，且时间上也是相对而言比较紧张，但好在比赛结束前成功封箱，最终也是获得了湖南省一等奖的好成绩。

下面附上作品的实物测试视频链接：

https://www.bilibili.com/video/BV1VtiueAEcK/?spm_id_from=333.999.0.0&vd_source=a0b00ddf466629a630c9f8aad4299f86

作品实物图片：

![4292c69c6455ec0243c205edc728475](https://github.com/user-attachments/assets/36f55c76-fea2-476e-906f-5be6fc68b310)

二、赛题分析

![image](https://github.com/user-attachments/assets/db31802e-9d39-4835-a166-e9b23019099e)
![image](https://github.com/user-attachments/assets/6b518bf3-7306-4c4a-bf92-d3e51214637f)
![image](https://github.com/user-attachments/assets/dc65bb75-87ff-4edf-af50-cfb426c7d72a)

分析题目要求
