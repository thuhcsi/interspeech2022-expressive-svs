---
layout: default
---
# Abstract

Previous works on expressive speech synthesis mainly focus on current sentence. The context in adjacent sentences is neglected, resulting in inﬂexible speaking style for the same text, which lacks speech variations. In this paper, we propose a hierarchical framework to model speaking style from context. A hierarchical context encoder is proposed to explore a wider range of contextual information considering structural relationship in context, including interphrase and inter-sentence relations. Moreover, to encourage this encoder to learn style representation better, we introduce a novel training strategy with knowledge distillation, which provides the target for encoder training. Both objective and subjective evaluations on a Mandarin lecture dataset demonstrate that the proposed method can signiﬁcantly improve the naturalness and expressiveness of the synthesized speech.

# Subjective Evaluation 
To demonstrate that our proposed model can significantly improve the naturalness and expressiveness of the synthesized speech, some samples are provided for comparison. **GT** means ground truth. **FastSpeech 2** means  original FastSpeech 2 with several changes consistent to the proposed model, and **XLNET-FastSpeech 2** means FastSpeech 2 with a plain context encoder without the use of inter-sentence relations, which are described in detail in the paper. In addition, a well-trained HIFI-GAN is used as the vocoder to generate waveform.

| Target Chinese Text | GT | FastSpeech 2 | XLNET-FastSpeech2 | Proposed |
| :---- | :---- | :---- | :---- | :---- |
| 那学着学着学着，是不是有一种望洋兴叹的感觉？ | <audio controls><source src="./wavs/gt/0.wav" type="audio/wav">Your browser does not support the audio element.</audio> | <audio controls><source src="./wavs/fs2/0.wav" type="audio/wav">Your browser does not support the audio element.</audio> | <audio controls><source src="./wavs/xlnet-fs2/0.wav" type="audio/wav">Your browser does not support the audio element.</audio> | <audio controls><source src="./wavs/proposed/0.wav" type="audio/wav">Your browser does not support the audio element.</audio> |
| 而恰恰是因为学的深，反而有可能过不了。 | <audio controls><source src="./wavs/gt/1.wav" type="audio/wav">Your browser does not support the audio element.</audio> | <audio controls><source src="./wavs/fs2/1.wav" type="audio/wav">Your browser does not support the audio element.</audio> | <audio controls><source src="./wavs/xlnet-fs2/1.wav" type="audio/wav">Your browser does not support the audio element.</audio> | <audio controls><source src="./wavs/proposed/1.wav" type="audio/wav">Your browser does not support the audio element.</audio> |
| 这两种观点在今后我们所有的刑法问题中大家都会看到它们的分析。 | <audio controls><source src="./wavs/gt/4.wav" type="audio/wav">Your browser does not support the audio element.</audio> | <audio controls><source src="./wavs/fs2/4.wav" type="audio/wav">Your browser does not support the audio element.</audio> | <audio controls><source src="./wavs/xlnet-fs2/4.wav" type="audio/wav">Your browser does not support the audio element.</audio> | <audio controls><source src="./wavs/proposed/4.wav" type="audio/wav">Your browser does not support the audio element.</audio> |
| 从实质上来看，冒充军警人员抢劫都要判十年以上，那真警察抢劫是不更应该处十年以上了，是不这意思。 | <audio controls><source src="./wavs/gt/5.wav" type="audio/wav">Your browser does not support the audio element.</audio> | <audio controls><source src="./wavs/fs2/5.wav" type="audio/wav">Your browser does not support the audio element.</audio> | <audio controls><source src="./wavs/xlnet-fs2/5.wav" type="audio/wav">Your browser does not support the audio element.</audio> | <audio controls><source src="./wavs/proposed/5.wav" type="audio/wav">Your browser does not support the audio element.</audio> |
| 在二审期间那么就应该撤销案件啊宣判无罪。                     | <audio controls><source src="./wavs/gt/8.wav" type="audio/wav">Your browser does not support the audio element.</audio> | <audio controls><source src="./wavs/fs2/8.wav" type="audio/wav">Your browser does not support the audio element.</audio> | <audio controls><source src="./wavs/xlnet-fs2/8.wav" type="audio/wav">Your browser does not support the audio element.</audio> | <audio controls><source src="./wavs/proposed/8.wav" type="audio/wav">Your browser does not support the audio element.</audio> |
| 但是我希望大家采取阶层论也要尊重四要件。                     | <audio controls><source src="./wavs/gt/10.wav" type="audio/wav">Your browser does not support the audio element.</audio> | <audio controls><source src="./wavs/fs2/10.wav" type="audio/wav">Your browser does not support the audio element.</audio> | <audio controls><source src="./wavs/xlnet-fs2/10.wav" type="audio/wav">Your browser does not support the audio element.</audio> | <audio controls><source src="./wavs/proposed/10.wav" type="audio/wav">Your browser does not support the audio element.</audio> |


* * *


# Ablation Study 
### Investigation on knowledge distillation training strategy

| Target Chinese Text | Proposed | without knowledge distillation |
| :---- | :---- | :---- |
| 那学着学着学着，是不是有一种望洋兴叹的感觉？ | <audio controls><source src="./wavs/cmos1/1.wav" type="audio/wav">Your browser does not support the audio element.</audio> | <audio controls><source src="./wavs/cmos1/-1.wav" type="audio/wav">Your browser does not support the audio element.</audio> |
| 当然可以，只是从人道主义考虑因为他在日本已经受过刑。 | <audio controls><source src="./wavs/cmos1/2.wav" type="audio/wav">Your browser does not support the audio element.</audio> | <audio controls><source src="./wavs/cmos1/-2.wav" type="audio/wav">Your browser does not support the audio element.</audio> |
| 这两种观点在今后我们所有的刑法问题中大家都会看到它们的分析。 | <audio controls><source src="./wavs/cmos1/3.wav" type="audio/wav">Your browser does not support the audio element.</audio> | <audio controls><source src="./wavs/cmos1/-3.wav" type="audio/wav">Your browser does not support the audio element.</audio> |
| 但是我希望大家采取阶层论也要尊重四要件。 | <audio controls><source src="./wavs/cmos1/4.wav" type="audio/wav">Your browser does not support the audio element.</audio> | <audio controls><source src="./wavs/cmos1/-4.wav" type="audio/wav">Your browser does not support the audio element.</audio> |

### Investigation on hierarchical context encoder

| Target Chinese Text | Proposed | without hierarchical context encoder |
| :---- | :---- | :---- |
| 啊，这个成绩是什么呢？客观题。 | <audio controls><source src="./wavs/cmos2/1.wav" type="audio/wav">Your browser does not support the audio element.</audio> | <audio controls><source src="./wavs/cmos2/-1.wav" type="audio/wav">Your browser does not support the audio element.</audio> |
| 它其实属于第几款呢？ | <audio controls><source src="./wavs/cmos2/2.wav" type="audio/wav">Your browser does not support the audio element.</audio> | <audio controls><source src="./wavs/cmos2/-2.wav" type="audio/wav">Your browser does not support the audio element.</audio> |
| 叫余平故意泄露国家秘密罪。 | <audio controls><source src="./wavs/cmos2/3.wav" type="audio/wav">Your browser does not support the audio element.</audio> | <audio controls><source src="./wavs/cmos2/-3.wav" type="audio/wav">Your browser does not support the audio element.</audio> |
| 但现在同学们学了刑法。 | <audio controls><source src="./wavs/cmos2/4.wav" type="audio/wav">Your browser does not support the audio element.</audio> | <audio controls><source src="./wavs/cmos2/-4.wav" type="audio/wav">Your browser does not support the audio element.</audio> |
| 我们不要对自己抱以太高的期望。 | <audio controls><source src="./wavs/cmos2/5.wav" type="audio/wav">Your browser does not support the audio element.</audio> | <audio controls><source src="./wavs/cmos2/-5.wav" type="audio/wav">Your browser does not support the audio element.</audio> |


* * *


# Case Study
To explore the impact of contextual information on the expressiveness of synthesized speech, a case study is conducted to synthesize the same utterance with different context: i) using ground-truth context (original context); ii) randomly selecting 4 sentences and itself as context (irrelevant context); iii) using current sentence only (no context).


| Context | Target Chinese Text | Audio | Mel-Spectrogram |
| :---- | :---- | :---- | :---: |
| original context | 因为大家一定要注意。 | <audio controls><source src="./wavs/casestudy/proposed.wav" type="audio/wav">Your browser does not support the audio element.</audio> | <img src="./wavs/casestudy/proposed.png" width="25%"> |
| irrelevant context | 因为大家一定要注意。 | <audio controls><source src="./wavs/casestudy/random.wav" type="audio/wav">Your browser does not support the audio element.</audio> | <img src="./wavs/casestudy/random.png" width="25%"> |
| no context | 因为大家一定要注意。 | <audio controls><source src="./wavs/casestudy/self.wav" type="audio/wav">Your browser does not support the audio element.</audio> | <img src="./wavs/casestudy/self.png" width="25%"> |

