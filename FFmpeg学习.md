# FFmpeg学习

## 命令行

### 常用参数

#### -i

在FFmpeg中，"-i"参数用于**指定输入文件或输入流**。它是一个**必需的参数**，表示输入文件或流的位置和类型。该参数后面应该**跟着输入文件或流的路径或URL**。

例如，假设我们要**转换**一个名为"input.mp4"的**视频文件为另一个格式**，我们可以使用以下命令：

```cmd
ffmpeg -i input.avi output.mp4
```

"-i"参数用于指定输入文件"input.mp4"，而"output.avi"则是转换后的输出文件。请注意，如果**输入文件的路径或名称中包含空格或其他特殊字符，应该<u>使用引号将其括起来</u>**。



此外，"-i"参数也可以用于**指定从输入流中读取数据**。例如，我们可以使用以下命令**从网络摄像头中捕获视频流**：

```cmd
ffmpeg -i rtsp://192.168.1.1/stream output.mp4
```

在这个命令中，"-i"参数指定从网络摄像头的RTSP流中读取数据，并将其保存为"output.mp4"文件。

简而言之，"-i"参数是FFmpeg中非常重要的一个参数，它**用于指定输入文件或流，是使用FFmpeg进行音视频处理的<u>必需参数</u>**。





#### -f

在FFmpeg中，"-f"参数用于**指定输出格式**。它是一个**可选参数**，如果不指定，则<u>FFmpeg将根据输出文件的扩展名猜测输出格式</u>。

例如，假设我们要将一个名为"input.mp4"的视频文件转换为"output.avi"格式，我们可以使用以下命令：

```cmd
ffmpeg -i input.mp4 -f avi output.avi
```

在这个命令中，"-i"参数用于指定输入文件"input.mp4"，而"-f"参数则用于指定输出格式为"avi"，"output.avi"是转换后的输出文件。

请注意，不是所有的格式都能够被FFmpeg所支持。如果你不确定输出格式的类型或参数，可以使用"ffmpeg -formats"命令列出所有可用的输出格式。

除了"-f"参数外，还有一些其他的输出参数可以进行配置，例如"-b:v"、"-s"、"-r"等，这些参数可以对输出文件的比特率、分辨率、帧率等进行配置。

简而言之，"-f"参数是FFmpeg中用于**指定输出格式的一个可选参数，它可以帮助我们控制输出文件的格式和类型**。





#### -b:v

在FFmpeg中，"-b:v"参数用于**指定输出视频的比特率**。它是一个**可选参数**，用于<u>控制输出视频文件的码率</u>，也就是视频数据每秒钟的平均比特数。该参数的值可以是固定比特率（如10M）或变量比特率（如2000k）。

例如，假设我们要将一个名为"input.mp4"的视频文件转换为"output.avi"格式，并将输出文件的比特率设置为2Mbps，我们可以使用以下命令：

```cmd
ffmpeg -i input.mp4 -b:v 2M output.avi
```

在这个命令中，"-i"参数用于指定输入文件"input.mp4"，而"-b:v"参数则用于**指定输出视频的比特率为2Mbps**，"output.avi"是转换后的输出文件。

请注意，输出文件的比特率并不是越高越好。**过高**的比特率可能会导致**文件过大、上传下载缓慢、播放卡顿**等问题，而**过低**的比特率则可能导致**视频质量下降、画面模糊**等问题。因此，应该根据具体的需求和情况，选择合适的比特率。

除了"-b:v"参数外，还有一些其他的输出参数可以进行配置，例如"-s"、"-r"、"-c:v"等，这些参数可以对输出文件的分辨率、帧率、编码格式等进行配置。

简而言之，"-b:v"参数是FFmpeg中用于**指定输出视频比特率的一个可选参数，它可以帮助我们控制输出视频文件的码率和文件大小**。





#### -bufsize

在FFmpeg中，"-bufsize"参数用于**设置视频编码器缓冲区的大小，以控制输出视频的码率和视频质量**。该参数是一个**可选参数**，单位为比特数（bit）。

视频编码器将输入视频的原始数据进行编码，生成压缩后的视频数据。**编码器缓冲区是编码器在编码过程中用来存储数据的区域，当缓冲区中的数据达到一定数量时，编码器才会将数据写入输出文件。通过设置缓冲区大小，可以控制编码器输出数据的速度和质量**。

例如，假设我们要将一个名为"input.mp4"的视频文件转换为"output.avi"格式，并设置输出视频的比特率为2Mbps，缓冲区大小为2M，我们可以使用以下命令：

```cmd
ffmpeg -i input.mp4 -b:v 2M -bufsize 2M output.avi
```

在这个命令中，"-i"参数用于指定输入文件"input.mp4"，"-b:v"参数用于指定输出视频的比特率为2Mbps，而"-bufsize"参数则用于设置视频编码器缓冲区的大小为2M，"output.avi"是转换后的输出文件。

请注意，如果缓冲区大小设置得**过小**，则可能会导致**视频质量下降或出现卡顿**等问题；如果设置得**过大**，则可能会导致**编码器延迟增加、处理速度变慢**等问题。因此，应该根据具体的需求和情况，选择合适的缓冲区大小。

除了"-bufsize"参数外，还有一些其他的输出参数可以进行配置，例如"-s"、"-r"、"-b:a"等，这些参数可以对输出文件的分辨率、帧率、音频比特率等进行配置。

简而言之，"-bufsize"参数是FFmpeg中用于设置视频编码器缓冲区大小的一个可选参数，它可以帮助我们控制输出视频的码率和质量。

>  **注：**
>
>  在FFmpeg中，**当使用"-b:v"参数指定输出视频的比特率时，建议同时使用"-bufsize"参数设置视频编码器缓冲区的大小，并且两个参数的值一般应该相同**。这是因为：
>
>  1. 视频编码器需要在缓冲区中积累一定数量的数据才能进行编码，如果缓冲区太小，可能导致编码器无法及时处理输入数据，从而影响输出视频的质量。
>  2. 输出视频的比特率和视频编码器缓冲区的大小密切相关。如果输出视频的比特率较高，但缓冲区太小，可能会导致缓冲区溢出，从而导致数据丢失或视频质量下降。相反，如果输出视频的比特率较低，但缓冲区太大，可能会导致编码器延迟增加，从而影响输出视频的处理速度和质量。
>
>  因此，建议在使用"-b:v"参数时，同时使用"-bufsize"参数，并将它们的值设置为相同的大小。这样可以**确保视频编码器有足够的缓冲区来存储输入数据，并在输出视频的质量和处理速度之间取得一个平衡**。
>
>  需要注意的是，缓冲区大小的设置还受到其他因素的影响，例如视频分辨率、帧率、编码格式等。因此，应该根据具体的需求和情况，选择合适的缓冲区大小。





#### 	-r

在FFmpeg中，"-r"参数可以用于**指定输入视频的帧率和输出视频的帧率**。该参数是一个**可选参数**，单位是帧率。如果在输入视频时使用"-r"参数，则指定输入视频的帧率；如果在输出视频时使用"-r"参数，则指定输出视频的帧率。

例如，以下命令可以将名为"input.mp4"的视频文件转换为"output.avi"格式，并将输出视频的帧率设置为25fps：	

```cmd
ffmpeg -i input.mp4 -r 25 output.avi
```

在这个命令中，"-i"参数用于指定输入文件"input.mp4"，而"-r"参数用于设置输出视频的帧率为25fps。

如果要指定输入视频的帧率，则可以使用以下命令：

```cmd
ffmpeg -r 25 -i input.mp4 output.avi
```

在这个命令中，"-r"参数用于指定输入视频的帧率为25fps，"-i"参数用于指定输入文件"input.mp4"，而"output.avi"是转换后的输出文件。

需要注意的是，输入视频的帧率和输出视频的帧率应该相匹配，否则可能会导致视频播放速度变快或变慢，甚至出现视频画面断层的问题。因此，在使用"-r"参数时，应该**确保与输入视频的帧率或者输出视频的帧率相同，并根据实际需求进行调整**。





#### -s

在FFmpeg中，"-s"参数用于**设置输出视频的分辨率**，该参数是一个**可选参数**。

例如，如果要将名为"input.mp4"的视频文件转换为"output.avi"格式，并将输出视频的分辨率设置为640x480，可以使用以下命令：

```cmd
ffmpeg -i input.mp4 -s 640x480 output.avi
```

在这个命令中，"-i"参数用于指定输入文件"input.mp4"，而"-s"参数用于设置输出视频的分辨率为640x480，"output.avi"是转换后的输出文件。

需要注意的是，**分辨率的大小会影响视频的清晰度和文件大小，分辨率越高，视频越清晰，文件大小也越大**。在使用"-s"参数时，应该根据实际需求进行调整。

除了"-s"参数外，还有一些其他的输出参数可以进行配置，例如"-r"、"-b:v"、"-bufsize"等，这些参数可以对输出文件的帧率、比特率、缓冲区大小等进行配置。

简而言之，"-s"参数是FFmpeg中用于设置输出视频的分辨率的一个重要参数，它可以**帮助我们控制输出视频的清晰度和文件大小。在使用该参数时，应该根据实际需求进行调整。**





#### -c:v

在FFmpeg中，"-c:v"参数用于**设置视频编解码器**（Video Codec），该参数是一个**可选参数**。它**指定了用于编码输出视频的编解码器**。编解码器是一种能够将视频压缩为较小文件大小的算法，同时保持视频质量的方法。

在FFmpeg中，有许多不同的视频编解码器可供选择，例如H.264、MPEG-4、VP8、VP9等等。在使用"-c:v"参数时，需要输入所需的编解码器名称或者ID。可以通过"-encoders"命令查看所有可用的视频编解码器，例如：

```cmd
ffmpeg -encoders | findstr video
```



例如，如果要将名为"input.mp4"的视频文件转换为"output.avi"格式，并**将输出视频的编码器设置为MPEG-4**（使用libxvid编解码器），可以使用以下命令：

```cmd
ffmpeg -i input.mp4 -c:v libxvid -q:v 3 output.avi
```

在这个命令中，"-i"参数用于指定输入文件"input.mp4"，而**"-c:v"参数用于设置输出视频的编码器为MPEG-4，使用libxvid编解码器。"-q:v"参数用于设置输出视频的质量，数字越小质量越高，3是一个常见的中等质量值**。"output.avi"是转换后的输出文件。

需要注意的是，不同的编码器具有不同的特点和性能，而且它们也可能具有不同的版权和许可证要求。因此，在选择编码器时，应该根据实际需求和考虑其他方面的因素进行选择。如果不指定编码器，则FFmpeg会**根据输出文件的扩展名自动选择一个默认编码器**。

除了"-c:v"参数外，还有一些其他的编解码器参数可以进行配置，例如"-b:v"、"-bufsize"、"-preset"等，这些参数可以对输出视频的比特率、缓冲区大小、编码速度等进行配置。

简而言之，"-c:v"参数是FFmpeg中用于**设置输出视频编解码器的一个重要参数，它可以帮助我们选择合适的编解码器来实现视频的压缩和保证视频质量**。在使用该参数时，应该根据实际需求进行调整。



#### -c:a

在FFmpeg中，"-c:a"参数是用于设置输出音频编解码器的参数，该参数是一个**可选参数**。它可以指定输出文件的音频编码器，让FFmpeg将输入音频流从一种格式转换为另一种格式。

在使用该参数时，需要输入所需的音频编解码器名称或者ID。可以通过"-encoders"命令查看所有可用的音频编解码器，例如：

```cmd
ffmpeg -encoders | findstr audio
```



举个例子，如果要将名为"input.mp3"的音频文件转换为"output.ogg"格式，并使用vorbis编解码器进行编码，可以使用以下命令：

```cmd
ffmpeg -i input.mp3 -c:a libvorbis output.ogg
```

在这个命令中，"-i"参数用于指定输入文件"input.mp3"，而"-c:a"参数用于设置输出音频的编码器为vorbis，使用libvorbis编解码器。"output.ogg"是转换后的输出文件。

除了"-c:a"参数外，还有一些其他的音频编解码器参数可以进行配置，例如"-b:a"、"-ar"、"-ac"等，这些参数可以对输出音频的比特率、采样率、声道数等进行配置。

需要注意的是，不同的音频编解码器具有不同的特点和性能，而且它们也可能具有不同的版权和许可证要求。因此，在选择编码器时，应该根据实际需求和考虑其他方面的因素进行选择。如果不指定编码器，则FFmpeg会根据输出文件的扩展名自动选择一个默认编码器。

简而言之，"-c:a"参数是FFmpeg中用于**设置输出音频编解码器的一个重要参数，它可以帮助我们选择合适的编解码器来实现音频的压缩和保证音频质量**。在使用该参数时，应该根据实际需求进行调整。





#### -vf

在 FFmpeg 中，-vf（video filter）参数用于指定视频过滤器。通过使用-vf参数，可以将多个过滤器以逗号分隔的形式串联在一起。过滤器可以用于修改视频的帧率、大小、格式等属性，或者应用各种效果和滤镜来增强视频的质量。

> 注:
>
> 在使用 FFmpeg 进行视频处理时，可以使用 `-filter_complex` 或 `-vf` 参数来指定视频过滤器。这两个参数的作用是一样的，都用于指定视频过滤器，写法不同。
>
> `-vf` 参数用于指定简单的线性滤镜链，适用于只有一种输入和输出的情况。例如，下面的命令将视频裁剪到宽度为 100 像素：
>
> ```
> cssCopy code
> ffmpeg -i input.mp4 -vf crop=100:in_h output.mp4
> ```
>
> `-filter_complex` 参数用于指定复杂的过滤器图形，适用于多输入和多输出的情况。例如，下面的命令将两个视频拼接在一起：
>
> ```
> lessCopy code
> ffmpeg -i input1.mp4 -i input2.mp4 -filter_complex "[0:v] [0:a] [1:v] [1:a] concat=n=2:v=1:a=1 [v] [a]" -map "[v]" -map "[a]" output.mp4
> ```
>
> 虽然 `-vf` 和 `-filter_complex` 的作用是一样的，但是 `-vf` 的使用比较简单，适用于只有一种输入和输出的情况，而 `-filter_complex` 则适用于多输入和多输出的情况。





#### -ac

在FFmpeg中，"-ac"参数用于**设置输出音频流的声道数的参数**，该参数是一个**可选参数**。它可以指定输出文件的声道数，从而使FFmpeg将输入音频流从一种声道数转换为另一种声道数。

在使用该参数时，需要输入所需的声道数，可以是一个整数，也可以是一个特定的声道布局。例如，"-ac 2"表示输出文件应该是双声道的，"-ac 1"表示输出文件应该是单声道的。如果要将多声道音频流转换为单声道音频流，可以使用以下命令：

```cmd
ffmpeg -i input.wav -ac 1 output.wav
```

在这个命令中，"-i"参数用于指定输入文件"input.wav"，而"-ac"参数用于设置输出音频流的声道数为1，也就是单声道。"output.wav"是转换后的输出文件。

需要注意的是，"-ac"参数只是用于设置输出文件的声道数，不同的声道数可能会影响音频的质量和大小。在进行音频转换时，应该根据实际需求和其他因素进行选择。如果不指定"-ac"参数，则FFmpeg会使用默认的声道数进行转换，一般情况下默认值为输入音频流的声道数。

简而言之，"-ac"参数是FFmpeg中用于设置输出音频流声道数的一个重要参数，它可以帮助我们**实现音频流的格式转换和声道数调整**。在使用该参数时，应该根据实际需求进行调整。





#### -ar

在FFmpeg中，"-ar"参数用于**设置输出音频流的采样率的参数**，该参数是一个**可选参数**。采样率是指在一定时间内对声音信号进行采样的次数，采样率越高，声音的还原效果就越好，但是文件大小也会相应增加。

在使用该参数时，需要输入所需的采样率，可以是一个整数。例如，"-ar 44100"表示输出文件应该有44.1kHz的采样率，这是CD音频标准的采样率。如果要将输入文件的采样率降低到22050Hz，可以使用以下命令：

```cmd
ffmpeg -i input.wav -ar 22050 output.wav
```

在这个命令中，"-i"参数用于指定输入文件"input.wav"，而"-ar"参数用于设置输出音频流的采样率为22050Hz，也就是将采样率降低到一半。"output.wav"是转换后的输出文件。

需要注意的是，"-ar"参数只是用于设置输出文件的采样率，不同的采样率可能会影响音频的质量和大小。在进行音频转换时，应该根据实际需求和其他因素进行选择。如果不指定"-ar"参数，则FFmpeg会使用默认的采样率进行转换，一般情况下**默认值为输入音频流的采样率**。

简而言之，"-ar"参数是FFmpeg中用于**设置输出音频流采样率**的一个重要参数，它可以帮助我们实现音频流的格式转换和采样率调整。在使用该参数时，应该根据实际需求进行调整。





#### -filter_complex

在FFmpeg中，"-filter_complex"参数用于**应用复杂滤镜**的参数。在视频编辑和处理过程中，滤镜是非常重要的工具，它可以帮助我们**实现各种特效和效果**。在FFmpeg中，滤镜可以应用于音频、视频或复合流，而"-filter_complex"参数则是用于应用复杂滤镜的场景。

复杂滤镜是由多个简单滤镜组合而成的滤镜，它可以实现更加复杂的特效和处理效果。在使用"-filter_complex"参数时，需要使用一些特殊的语法来描述滤镜的结构和参数，例如：

```cmd
ffmpeg -i input.mp4 -filter_complex "[0:v]scale=640x360,transpose=1[v];[0:a]volume=2.0[a]" -map "[v]" -map "[a]" output.mp4
```

在这个命令中，"-i"参数用于指定输入文件"input.mp4"，而"-filter_complex"参数用于应用复杂滤镜。在这个滤镜中，**输入文件的视频流通过"scale"滤镜进行缩放，然后通过"transpose"滤镜进行旋转。音频流则通过"volume"滤镜进行音量调整**。最后，"-map"参数用于指定输出文件中需要包含哪些流，这里将视频流和音频流分别映射到了输出文件的"v"和"a"标签中。

需要注意的是，复杂滤镜的语法和参数比较复杂，需要掌握一定的FFmpeg知识和滤镜语法。在实际使用中，可以参考官方文档和其他资料，或者查看FFmpeg提供的示例代码。同时，也可以通过多次实践和调试来掌握复杂滤镜的使用方法和技巧。



#### -q:a

在FFmpeg中，`-q:a`参数用于指定音频的质量，取值范围为0到9，其中0为最高质量，9为最低质量。这个参数只在一些编码器（如libmp3lame、libopus、libvorbis）下起作用。

具体地说，这个参数会影响编码器的比特率控制。通常情况下，比特率越高，音频质量越好，但文件大小也越大。如果使用`-q:a`参数，编码器将会根据所指定的质量级别自动选择合适的比特率来进行编码，从而在一定程度上平衡音频质量和文件大小。

需要注意的是，不同编码器对`-q:a`参数的解释可能会有所不同，因此在使用时应该查看具体编码器的文档或者测试不同参数值所得到的音频质量和文件大小，以便选择最适合的参数。





#### -preset

在FFmpeg中，"-preset"参数用于**指定编码速度和质量之间平衡的参数**。在视频编码的过程中，编码速度和编码质量之间往往存在着一定的平衡关系，如果希望提高编码速度，可能会牺牲一定的编码质量；反之亦然。而"-preset"参数则是用于控制这种平衡的关键参数之一。

具体来说，"-preset"参数会影响到编码器的多个参数和设置，从而影响编码速度和质量。在FFmpeg中，常见的"-preset"参数包括：

- ultrafast
- superfast
- veryfast
- faster
- fast
- medium
- slow
- slower
- veryslow

这些参数分别代表了编码速度和质量的不同权衡关系。一般来说，速度越快，编码质量可能会越差；速度越慢，编码质量可能会越好。具体选择哪个"-preset"参数，需要根据具体的需求和应用场景进行权衡。

例如，以下命令中的"-preset fast"参数指定了编码速度较快，编码质量适中的参数：

```cmd
ffmpeg -i input.mp4 -c:v libx264 -preset fast -b:v 1M -c:a copy output.mp4
```

在这个命令中，"-i"参数用于指定输入文件"input.mp4"，**"-c:v"参数用于指定视频编码器为"libx264"，"-preset"参数用于指定编码速度和质量之间的平衡参数为"fast"，"-b:v"参数用于指定视频流的码率为1M，"-c:a"参数用于直接拷贝音频流**。最后，输出文件保存为"output.mp4"。

需要注意的是，"-preset"参数只是影响编码速度和质量之间的平衡关系，具体的编码效果还需要根据其他参数进行调整和优化。在实际使用中，需要结合具体的应用场景和需求来选择合适的"-preset"参数和其他编码参数。

> `-preset ultrafast` 和 `-preset placebo` 是在使用 FFmpeg 进行视频编码时的预设参数。这些预设参数用于控制编码速度和压缩效率之间的权衡。
>
> 1. `-preset ultrafast`: 这是一个编码速度优先的预设参数。使用此预设参数可以快速完成编码过程，但可能会导致视频质量较低和较大的文件大小。适用于需要快速编码的场景，如实时流传输或测试目的。
> 2. `-preset placebo`: 这是一个编码质量优先的预设参数。使用此预设参数可以获得最高质量的视频输出，但编码速度非常慢，需要更长的时间来完成编码。适用于对视频质量要求极高的场景，如专业视频制作或存档目的。
>
> 这些预设参数是 FFmpeg 中提供的一组预定义选项，可以根据具体需求选择合适的预设参数。除了 ultrafast 和 placebo 外，还有其他预设参数可供选择，例如 veryfast、fast、slow 等，用于在编码速度和质量之间进行平衡。





#### -c copy

在FFmpeg中，"-copy"参数**用于指定复制某个流，不进行编码处理，直接将该流复制到输出文件中，从而节省编码的时间和计算资源，同时保持原始数据的质量**。"-copy"参数也可以写成"-c copy"。

具体地说，"-c copy"参数可以用于音视频编解码中的多个场景，例如：

1.复制音频流或视频流：如果输入文件中已经包含了需要的音频流或视频流，可以使用"-c copy"参数直接将该流复制到输出文件中，而无需进行任何编码处理。例如，以下命令将输入文件中的音频流直接复制到输出文件中：

```cmd
ffmpeg -i input.mp4 -c:a copy output.mp4
```

在这个命令中，"-i"参数用于指定输入文件"input.mp4"，"-c:a"参数用于指定音频编码器为复制（即不进行编码处理），"-copy"参数用于复制音频流到输出文件中，最后输出文件保存为"output.mp4"。

2.复制字幕流：如果输入文件中包含了字幕流，可以使用"-c copy"参数将该字幕流复制到输出文件中。例如，以下命令将输入文件中的字幕流复制到输出文件中：

```cmd
ffmpeg -i input.mp4 -c:s copy output.mp4
```

在这个命令中，"-i"参数用于指定输入文件"input.mp4"，"-c:s"参数用于指定字幕编码器为复制（即不进行编码处理），"-copy"参数用于复制字幕流到输出文件中，最后输出文件保存为"output.mp4"。

需要注意的是，"-c copy"参数**只能用于将某一种流复制到输出文件中，而无法进行流的混合或转换**，如果需要对流进行混合或转换，需要使用其他编码器和参数进行处理。





#### -acodec copy

1. `-acodec copy`用于复制音频流，即将源文件中的音频流直接复制到输出文件中，不进行任何编码或转码操作。

2. 这个选项只适用于音频流，而不会对视频流进行任何处理。

   示例：

   ```cmd
   ffmpeg -i input.mp4 -acodec copy -vcodec <video_codec> output.mp4
   ```





#### -vcodec copy

1. `-vcodec copy`用于复制视频流，即将源文件中的视频流直接复制到输出文件中，不进行任何编码或转码操作。

2. 这个选项只适用于视频流，而不会对音频流进行任何处理。

   示例：

   ```cmd
   ffmpeg -i input.mp4 -vcodec copy -acodec <audio_codec> output.mp4
   ```

   



#### -ss

在FFmpeg中，"-ss"  参数表示**跳过输入文件的指定时间，从指定时间开始进行处理**。具体来说，它用于指定从哪个时间点开始剪辑或处理视频，其后面跟着一个时间戳参数，格式为"hh:mm:ss"或"ss"。

例如，如果需要从一个视频文件的 1 分 30 秒处开始剪辑，则可以使用以下命令：

```cmd
ffmpeg -i input.mp4 -ss 00:01:30 -c copy output.mp4
```

在这个命令中，"-i" 参数用于指定输入文件 "input.mp4"，"-ss" 参数用于指定从 1 分 30 秒的位置开始剪辑，"-c copy" 参数用于将剪辑后的视频流复制到输出文件中，最后输出文件保存为 "output.mp4"。

需要注意的是，"-ss" 参数一般必须放在 "-i" 参数之前，否则可能会导致剪辑不准确或处理失败(上面这个例子就不太好！)。另外，由于视频的编码方式不同，对于一些编码方式，" -ss" 参数可能会不够精确，因此需要结合其他参数一起使用。

> 注：
>
> 如果 "-ss" 参数放在 "-i" 参数之后，FFmpeg 会先读取完整的输入文件，然后再跳转到指定时间戳进行处理。这可能会导致剪辑不准确或处理失败，原因如下：
>
> 1. FFmpeg 需要先读取完整的输入文件才能确定指定时间戳的准确位置，这可能会导致处理速度变慢，尤其是对于大型视频文件来说。
> 2. 如果输入文件中包含多个视频流或音频流，则 FFmpeg 可能会选择错误的流进行处理，导致输出的结果不准确。
> 3. 如果输入文件的编码方式不支持随机访问或时间戳不准确，FFmpeg 可能无法准确跳转到指定时间戳，导致处理失败或输出的结果不准确。
>
> 因此，为了确保剪辑的准确性和处理效率，建议将 "-ss" 参数放在 "-i" 参数之前，这样 FFmpeg 就可以在读取输入文件时根据指定时间戳进行处理，避免了上述问题。



#### -vframe

在 FFmpeg 中，参数 `-vframes` 用于指定从视频中提取的帧数。它允许你设置提取的帧数的数量。

在之前的示例命令中，我们使用了 `-vframes 1` 来只提取一帧。这意味着从视频中仅提取一帧，并将其保存为输出文件。

如果你想提取多帧，只需将 `-vframes` 后面的数字更改为你想要的帧数。例如，要提取五帧，你可以使用 `-vframes 5`。这样会从视频中提取五帧，并将它们保存为输出文件的图片序列。

以下是使用FFmpeg命令行工具从视频中提取一帧并转换为BMP格式的示例命令：

```bash
ffmpeg -i input_video.mp4 -ss 00:00:05 -vframes 1 -f image2 output_frame.bmp
```

解释：

- `-i input_video.mp4`：指定输入视频文件。
- `-ss 00:00:05`：指定从视频中提取帧的时间点，此处为5秒，可以根据需要调整。
- `-vframes 1`：指定只提取一帧。
- `-f image2`：指定输出格式为图片序列，这里设置为BMP格式。
- `output_frame.bmp`：指定输出帧的文件名。

执行该命令后，FFmpeg将从输入视频中提取一帧，并将其保存为output_frame.bmp文件。请确保在使用之前已经安装了FFmpeg并且其在系统的环境变量中可用。



#### -t

在 FFmpeg 中，"-t" 参数用于**指定输出文件的时长或持续时间，即从输入文件中截取的时间长度。**

具体来说，"-t" 参数后面可以接一个以秒为单位的时间值，表示要从输入文件中截取的持续时间。例如：

```cmd
ffmpeg -i input.mp4 -t 10 output.mp4
```

上述命令表示从输入文件 "input.mp4" 中截取 10 秒钟的视频，并将结果保存为输出文件 "output.mp4"。



此外，"-t" 参数还可以与 "-ss" 参数一起使用，用于指定要截取的视频片段的起始时间和持续时间。例如：

```cmd
ffmpeg -i input.mp4 -ss 00:01:30 -t 10 output.mp4
```

上述命令表示从输入文件 "input.mp4" 中从第 1 分 30 秒开始截取 10 秒钟的视频，并将结果保存为输出文件 "output.mp4"。





#### -to

在 FFmpeg 中，"-to" 参数与 "-t" 参数类似，用于**指定输出文件的结束时间或持续时间**，即截取视频时结束的时间点。

具体来说，"-to" 参数后面可以接一个以秒为单位的时间值，表示要从输入文件中截取的持续时间，或者接一个时间戳，表示要从输入文件中截取到的结束时间点。例如：

```cmd
ffmpeg -i input.mp4 -to 00:01:30 output.mp4
```

上述命令表示从输入文件 "input.mp4" 中截取从开头到第 1 分 30 秒的视频，并将结果保存为输出文件 "output.mp4"。

需要注意的是，如果同时使用了 "-t" 和 "-to" 参数，FFmpeg 会以较小的值为准，即**以两者中最小的时间值为输出时长**。





#### -vn

在 FFmpeg 中，-vn 参数表示**只处理音频流，而不处理视频流**。**-vn 这个参数名中的 "vn" 其实是 "video null" 的缩写**，表示要禁用视频流。在处理视频文件时，FFmpeg 默认会处理视频和音频流。如果不使用 -vn 参数，FFmpeg 会将视频和音频流都处理完之后输出到目标文件中，这会导致生成的文件包含视频和音频两部分内容。

使用 -vn 参数可以让 FFmpeg 只处理音频流，从而**分离出视频文件中的音频部分**。这对于一些需要提取音频流的应用场景非常有用，例如从视频文件中提取音频进行处理、制作音频文件等等。

需要注意的是，-vn 参数只能用于分离音频流，无法用于分离视频流。如果需要分离视频流，可以使用类似 -an 参数来忽略音频流，只处理视频流。





#### -an

与`-vn` 同理咯





#### -map

在 FFmpeg 中，使用FFmpeg处理多媒体文件时 `-map` 参数来**选择从输入文件中复制哪些流并将它们写入输出文件**。通常在一个输入文件中会包含多个音频流、视频流、字幕流等不同类型的流，而输出文件中可能只需要其中的一部分流，或者需要对不同的流进行重编码等处理。

`-map`参数的基本语法为`-map [input_file_index]:[stream_specifier]`，其中`input_file_index`指定输入文件的**索引**，`stream_specifier`指定要复制或操作的**流的类型和索引**。例如，`-map 0:0`表示从第一个输入文件中选择第一个流，即第一个视频流；`-map 0:1`表示从第一个输入文件中选择第二个流，即第一个音频流。在`stream_specifier`中，常用的标识符包括`v`表示视频流，`a`表示音频流，`s`表示字幕流，数字表示具体的流索引等。

除了基本语法之外，`-map`参数还支持一些特殊的标识符，如`-map 0:a`表示从**第一个输入文件中选择所有的音频流**，`-map -0:v`表示**从所有输入文件中排除所有的视频流**等。





#### -tune

`-tune` 是FFmpeg中的一个选项，用于指定编码器的预设参数。它可以根据不同的应用场景和需求选择合适的预设参数，以优化编码质量、速度或特定的编码特性。

使用 `-tune` 选项可以提供以下预设参数：

1. `film`: 适用于电影内容的编码，注重编码质量。
2. `animation`: 适用于动画内容的编码，注重提供更好的动画压缩效果。
3. `grain`: 适用于具有颗粒状噪声的内容的编码，可以保留细节和噪声。
4. `stillimage`: 适用于静态图像内容的编码，注重保留图像细节。
5. `fastdecode`: 适用于快速解码的编码，可以加快解码速度。
6. `zerolatency`: 适用于实时传输场景的编码，尽量减小编码延迟。
7. `psnr`: 优化编码器以最大程度地提高峰值信噪比（PSNR）。

每个预设参数都针对特定的编码目标进行了优化，具体的效果和表现取决于输入内容、编码器以及其他相关参数的设置。

使用 `-tune` 选项时，可以根据实际需求选择合适的预设参数，以获得所需的编码效果。

> eg.：
>
> `-tune zerolatency` 是FFmpeg中的一个选项，用于优化编码设置以实现零延迟的实时传输。该选项适用于实时流媒体应用，例如视频会议、直播和实时监控等场景。
>
> 使用 `-tune zerolatency` 可以在一定程度上减少编码延迟，提高传输的实时性。它会对编码参数进行调整，以减小编码缓冲区的大小和延迟。具体来说，它可能会采取以下一些策略：
>
> 1. 减小GOP (Group of Pictures) 大小：GOP是一组连续的视频帧，减小GOP大小可以减小编码延迟，但也可能导致压缩效率和视频质量的降低。
> 2. 降低B帧的使用：B帧是一种参考两个关键帧之间的帧，减少B帧的使用可以减小编码延迟。
> 3. 使用较小的量化参数：量化参数的增加可以降低编码延迟，但也可能导致视频质量的降低。
> 4. 禁用某些编码优化：某些编码优化可能会引入额外的延迟，禁用这些优化可以减小编码延迟。
>
> 值得注意的是，使用 `-tune zerolatency` 可以降低编码延迟，但并不能完全实现零延迟，实际的延迟取决于多个因素，包括编码器设置、视频帧率、分辨率和编码质量等。
>
> 因此，在实时传输场景中，如果需要更低的编码延迟，可以尝试使用 `-tune zerolatency` 选项，并根据实际需求进行进一步调整和优化。



### 常用命令

#### 图片镜像

```cmd
ffmpeg -i input.jpg -vf hflip output.jpg
```

其中，`-i input.jpg` 指定输入图片文件路径为 `input.jpg`，`-vf hflip` 指定进行水平镜像操作，`output.jpg` 指定输出图片文件路径为 `output.jpg`。

如果需要进行垂直镜像操作，可以将 `-vf hflip` 替换为 `-vf vflip`。





#### 帧效果查看

```cmd
FFmpegStudy>ffplay -flags2 +export_mvs "[UHA-WINGS][Koi wa Ameagari no You ni][01][x264 1080p][GB].mp4" -vf codecview=mv=pf+bf+bb
```

使用 FFplay 工具来播放指定的 MP4 视频文件，并添加了 codecview 滤镜，通过设置 mv 参数可以显示每个宏块的运动矢量信息。

具体含义如下：

- `ffplay`：使用 FFplay 工具来播放视频
- `-flags2 +export_mvs`：启用 export_mvs 标志，允许输出每个宏块的运动矢量信息
- `"[UHA-WINGS][Koi wa Ameagari no You ni][01][x264 1080p][GB].mp4"`：指定要播放的 MP4 视频文件路径
- `-vf codecview=mv=pf`：添加 codecview 滤镜，并设置参数 mv=pf，以显示每个宏块的运动矢量信息。其中，mv 表示要显示运动矢量信息
- `pf`：在运动矢量图像上显示帧间预测（P帧）的矢量。
- `bf`：在运动矢量图像上显示前向预测帧（B帧）的矢量。
- `bb`：在运动矢量图像上显示双向预测帧（B帧）的矢量。





#### 切片（segment）

```cmd
ffmpeg -re -i input.mp4 -c copy -f segment -segment_format mp4 -segment_time 60 -segment_list_type m3u8 -segment_list output.m3u8 test_output-%d.mp4
```

该命令的功能是将输入的input.mp4文件**按照时长分割成若干个输出文件**test_output-1.mp4、test_output-2.mp4、test_output-3.mp4等，每个输出文件的时长是由-segment_time参数指定的，该参数的默认值为2秒。同时，由于-c copy参数的存在，输出文件的编码格式与输入文件相同，即不做重新编码处理，其次，-segment_format参数指定输出文件的格式为mp4。最后，-segment_list_type m3u8 -segment_list 生成指定的m3u8文件。

参数具体解释：

> - -re：以实时模式读取输入文件
> - -i input.mp4：输入文件为input.mp4
> - -c copy：进行复制编码，不对音视频进行重新编码，保留原有的编码格式和参数
> - -f segment：将输入流分割成多个输出段，每个输出段的时长由-segment_time参数决定
> - -segment_format mp4：指定输出段的格式为mp4格式
> - -segment_list_type m3u8：指定生成切片列表文档，文档格式为m3u8
> - segment_list output.m3u8：指定生成文档名为 output.m3u8（当然也可以指定为其他格式，诸如csv，flat等）
> - test_output-%d.mp4：输出文件的文件名格式，其中%d表示输出文件的序号，从1开始递增，每个输出段的时长由-segment_time参数决定。



注：使用-segment_time指定每60s进行一次切片时，并不能保证每个切片的时长都完全是60秒，因为ffmpeg默认在关键帧处进行切片，如果60秒的时长内没有关键帧，那么就会一直等到出现关键帧后再进行切片，所以可能会出现某些切片时长略短或略长的情况。这在对有长时间相同场景的音视频进行默认为2秒切片时，会特别明显，有些段会10多秒甚至更多，也有就1秒的。



#### 切片（-ss -t）

```cmd
ffmpeg -i "[UHA-WINGS][Koi wa Ameagari no You ni][01][x264 1080p][GB].mp4" -ss 5 -c copy -t 10 output_sst.mp4
```

将输入文件 "[UHA-WINGS] [Koi wa Ameagari no You ni] [01] [x264 1080p] [GB].mp4" 从第 5 秒的位置开始，复制 10 秒的内容，保存到输出文件 "output_sst.mp4" 中。

以下是每个参数的解释：

- `-i`：指定输入文件名。
- `"[UHA-WINGS][Koi wa Ameagari no You ni][01][x264 1080p][GB].mp4"`：输入文件名。
- `-ss 5`：从第 5 秒的位置开始。
- `-c copy`：使用“copy”编解码器，将输入文件中的音视频数据直接复制到输出文件中，以保持编码格式不变。
- `-t 10`：设置输出文件的持续时间为 10 秒。
- `output_sst.mp4`：输出文件名。





#### 音视频拆分

```cmd
ffmpeg -i "[UHA-WINGS][Koi wa Ameagari no You ni][01][x264 1080p][GB].mp4" -c:a copy -vn outputAudio.aac
```

将输入文件 "[UHA-WINGS] [Koi wa Ameagari no You ni] [01] [x264 1080p] [GB].mp4" 中的音频流提取出来，再将提取出来的音频流复制到输出文件 outputAudio.aac 中，而视频流则被丢弃。

具体的参数含义如下：

- `-i`：指定输入文件名；
- `-c:a`：指定要对音频流进行操作，这里表示对音频进行编码/解码（缺失参数）；
- `copy`：表示使用与输入流相同的编码格式，不进行编码，直接将输入流复制到输出文件；
- `-vn`：表示禁用视频流，不进行视频流的处理；
- `outputAudio.aac`：指定输出文件名为 outputAudio.aac。

因此，该命令的作用是提取输入文件中的音频流，直接将其复制到输出文件中，输出文件的格式为 AAC，视频流将被忽略。



```cmd
ffmpeg -i "[UHA-WINGS][Koi wa Ameagari no You ni][01][x264 1080p][GB].mp4" -c:v copy -an outputVideo.mp4
```

将输入文件 "[UHA-WINGS] [Koi wa Ameagari no You ni] [01] [x264 1080p] [GB].mp4" 中的视频流提取出来，再将提取出来的视频流复制到输出文件 outputVideo.mp4 中，而音频流则被丢弃。

具体的参数含义如下：

- `-i`：指定输入文件名；
- `-c:v`：指定要对音频流进行操作，这里表示对视频进行编码/解码（缺失参数）；
- `copy`：表示使用与输入流相同的编码格式，不进行编码，直接将输入流复制到输出文件；
- `-an`：表示禁用音频流，不进行音频的处理；
- `outputVideo.mp4`：指定输出文件名为 outputVideo.mp4。

因此，该命令的作用是提取输入文件中的视频流，直接将其复制到输出文件中，输出文件的格式为mp4，音频流将被忽略。





#### 抽帧

```cmd
ffmpeg -i input.mp4 -vf fps=10 out%d.jpg
```

该命令使用FFmpeg工具，将输入文件 input.mp4 的视频流以每秒10帧的速率抽取帧，并将抽取的每一帧保存为输出文件 out%d.jpg（%d 会被自动替换为数字序列）。

具体参数的作用如下：

- -i：指定输入文件名。
- -vf：指定视频滤镜，这里使用 fps=10 指定抽取帧的速率为**10帧/秒**。
- out%d.jpg：指定输出文件名，其中 %d 表示数字序列，会按照顺序递增，例如 out1.jpg、out2.jpg 等。



#### 音频编码质量

##### mp3

```cmd
ffmpeg -i outAnimal.mp3 -c:a libmp3lame -q:a 0 outAnimalMax.mp3
```

将输入音频文件 outAnimal.mp3 进行重新编码，转换为 MP3 格式的音频文件 outAnimalMax.mp3，同时对转码后的音频使用最高品质（音频质量系数为 0）进行编码。

各参数的意义如下：

- `-i outAnimal.mp3`：指定输入文件为 outAnimal.mp3。
- `-c:a libmp3lame`：设置音频编码器为 libmp3lame，即使用 LAME MP3 编码器对音频进行编码。
- `-q:a 0`：设置音频质量系数为 0，即使用最高音质对音频进行编码，生成的 MP3 文件质量最高。如果该参数设置为 2，则音频质量会有所降低，但生成的文件大小会更小。


## 音视频编解码

### 音视频解码

#### ffmpeg音视频解码流程参考

![](https://github.com/drizzledrop3/audio-video-learning/blob/main/IMG/AudioVideo/ffmpeg1.png)



#### ffmpeg音视频播放流程参考(windows)

![](https://github.com/drizzledrop3/audio-video-learning/blob/main/IMG/AudioVideo/ffmpeg2.png)



### 音视频编码

#### ffmpeg视频编码YUV参考

![](https://github.com/drizzledrop3/audio-video-learning/blob/main/IMG/AudioVideo/ffmpeg3.png)



#### ffmpeg音频编码PCM参考

![](https://github.com/drizzledrop3/audio-video-learning/blob/main/IMG/AudioVideo/ffmpeg4.png)




## FFmpeg开发库

### 简介

FFmpeg用于处理多媒体数据的开源软件项目，提供了多个库，其中的八个主要开发库如下：

1. **avcodec（编解码）**：
   - **作用**：提供了音视频编解码的功能，是 FFmpeg 中最重要的库之一。它包含了许多编码器和解码器，用于将音频和视频数据从一种格式转换为另一种格式。
2. **avformat（封装格式处理）**：
   - **作用**：处理多媒体封装格式，例如AVI、MP4、MKV等。它能够读取和写入这些封装格式，对媒体文件进行解封装和封装，提供了统一的接口。
3. **avfilter（滤镜特效处理）**：
   - **作用**：提供了音视频滤镜处理的功能，可以应用各种滤镜和特效，如裁剪、调整色彩、添加水印等。它允许在媒体流上构建处理链，实现复杂的处理流程。
4. **avdevice（各种设备的输入输出）**：
   - **作用**：用于处理各种设备的输入和输出，例如摄像头、麦克风等。它提供了一个通用的设备接口，使得 FFmpeg 能够与各种硬件设备进行交互。
5. **avutil（工具库）**：
   - **作用**：是 FFmpeg 中的工具库，包含了一些通用的工具函数和数据结构。其他库通常会依赖于 avutil 提供的基本功能，因此它是整个 FFmpeg 的基础。
6. **postproc（后加工）**：
   - **作用**：提供了一些图像后处理的功能，例如去块效应滤波、运动补偿等。它主要用于视频编码时对图像进行一些优化处理。但在现代 FFmpeg 中已不建议使用，因为大多数功能已经被 avfilter 取代。
7. **swresample（音频采样数据格式转换）**：
   - **作用**：用于进行音频采样数据的格式转换。它可以将音频数据从一种采样格式转换为另一种，例如从浮点数表示到整数表示，或者改变采样率。
8. **swscale（视频像素数据格式转换）**：
   - **作用**：用于进行视频像素数据的格式转换。它可以将视频帧的像素格式、尺寸等进行转换，以适应不同的需求，例如在不同的显示设备上播放视频。



### 应用举例

当使用 FFmpeg 的各个库进行实际开发时，可以涉及到以下一些使用例子：

1. **avcodec（编解码）**：
   - **例子**：将一个视频文件从一种编码格式（如 H.264）解码为另一种编码格式（如 H.265）。
   - **实际应用**：视频编辑软件、实时流媒体处理。

```c
AVFormatContext *inputFormatContext, *outputFormatContext;
AVCodecContext *decoderContext, *encoderContext;
AVPacket packet;
AVFrame *frame;

// 初始化和打开输入、输出格式上下文、编解码器等...

while (av_read_frame(inputFormatContext, &packet) >= 0) {
    // 解码视频帧
    avcodec_receive_frame(decoderContext, frame);
    
    // 对帧进行处理或修改
    
    // 编码并写入输出文件
    avcodec_send_frame(encoderContext, frame);
    av_write_frame(outputFormatContext, &packet);
}

// 清理资源...
```

在此示例中，展示avcodec用于视频帧解码、处理、编码，并将结果写入输出文件的基本框架。



2. **avformat（封装格式处理）**：
   - **例子**：将多个视频文件合并成一个。
   - **实际应用**：视频编辑、批量处理。

```c
AVFormatContext *inputFormatContext1, *inputFormatContext2, *outputFormatContext;
AVPacket packet;

// 初始化和打开输入、输出格式上下文等...

while (av_read_frame(inputFormatContext1, &packet) >= 0) {
    // 将第一个文件的帧写入输出文件
    av_write_frame(outputFormatContext, &packet);
}

while (av_read_frame(inputFormatContext2, &packet) >= 0) {
    // 将第二个文件的帧写入输出文件
    av_write_frame(outputFormatContext, &packet);
}

// 清理资源...
```

 在此示例中，展示avformat用于将两个输入文件的帧写入同一个输出文件的基本框架。



3. **avfilter（滤镜特效处理）**：
   - **例子**：为视频添加水印。
   - **实际应用**：视频编辑、广告插入。

```c
AVFilterGraph *filterGraph;
AVFilterContext *inputFilterContext, *outputFilterContext;
AVFrame *frame;

// 初始化和配置滤镜图...

while (av_read_frame(inputFormatContext, &packet) >= 0) {
    // 解码视频帧
    avcodec_receive_frame(decoderContext, frame);
    
    // 应用滤镜效果
    av_buffersrc_add_frame(inputFilterContext, frame);
    av_buffersink_get_frame(outputFilterContext, frame);
    
    // 编码并写入输出文件
    avcodec_send_frame(encoderContext, frame);
    av_write_frame(outputFormatContext, &packet);
}

// 清理资源...
```

在此示例中，展示avfilter用于视频滤镜处理的基本框架。



4. **avdevice（各种设备的输入输出）**：

   - **例子**：从摄像头捕获视频。

   - **实际应用**：实时视频采集、视频监控系统。

   ```c
   AVFormatContext *inputFormatContext;
   AVPacket packet;
   
   // 初始化和打开摄像头设备...
   
   while (av_read_frame(inputFormatContext, &packet) >= 0) {
       // 处理视频帧...
   }
   
   // 清理资源...
   ```

   在此示例中，avdevice用于从摄像头设备读取视频帧的基本框架。

   

5. **avutil（工具库）**：

   - **示例：** 获取多媒体文件的持续时间。
   - **实际应用：** 多媒体播放器，媒体信息工具。

   ```c
   codeAVFormatContext *formatContext;
   avformat_open_input(&formatContext, "input_file.mp4", NULL, NULL);
   avformat_find_stream_info(formatContext, NULL);
   
   int durationInSeconds = formatContext->duration / AV_TIME_BASE;
   printf("持续时间：%d 秒\n", durationInSeconds);
   
   // 清理资源...
   ```

   在此示例中，avutil 用于获取多媒体文件的持续时间的基本框架。

   

6. **postproc（后加工）**：

   - **示例：** 对视频帧应用后处理滤镜。
   - **实际应用：** 视频编辑，多媒体应用中的特效。

   ```c
   codeAVCodecContext *codecContext;
   AVFrame *inputFrame, *outputFrame;
   
   // 初始化编解码器和帧...
   
   // 将视频帧解码为 inputFrame
   
   // 应用后处理
   av_postproc_execute(codecContext->postproc, inputFrame->data, inputFrame->linesize, outputFrame->data, outputFrame->linesize, codecContext->width, codecContext->height);
   
   // 处理或显示输出帧
   
   // 清理资源...
   ```

   此示例演示了将后处理滤镜应用于视频帧的基本框架。

   

7. **swresample（音频采样数据格式转换）**：

   - **示例：** 将音频从一种采样率转换为另一种。
   - **实际应用：** 音频处理，与不同音频设备的兼容性。

   ```c
   codeSwrContext *swrContext;
   uint8_t **inputAudioData, **outputAudioData;
   
   // 初始化 swrContext 并分配 inputAudioData、outputAudioData...
   
   // 读取输入音频数据...
   
   // 重新采样音频
   swr_convert(swrContext, outputAudioData, outputFrameSize, (const uint8_t **)inputAudioData, inputFrameSize);
   
   // 处理或播放重新采样的音频
   
   // 清理资源...
   ```

   在此示例中，swresample 用于将音频数据从一种采样率转换为另一种的基本框架。

   

8. **swscale（视频像素数据格式转换）**：

- **示例：** 调整视频帧的分辨率。
- **实际应用：** 视频播放，视频编辑。

```c
codeSwsContext *swsContext;
AVFrame *inputFrame, *outputFrame;

// 初始化 swsContext 并分配 inputFrame、outputFrame...

// 将视频帧解码为 inputFrame

// 调整视频帧的分辨率
sws_scale(swsContext, inputFrame->data, inputFrame->linesize, 0, codecContext->height, outputFrame->data, outputFrame->linesize);

// 处理或显示缩放后的输出帧

// 清理资源...
```

在此示例中，swscale 用于调整视频帧的分辨率的基本框架。



### 结构体
[](https://github.com/drizzledrop3/audio-video-learning/blob/main/IMG/AudioVideo/FFmpegStruct.png)




## SDL开发库

### 简介



### 开发流程举例
[](https://github.com/drizzledrop3/audio-video-learning/blob/main/IMG/AudioVideo/SDL%E6%B5%81%E7%A8%8B%E5%9B%BE.png)
以`SDL播放YUV测试`为例，说明以上函数：

1. `SDL_Init(SDL_INIT_VIDEO)`: 初始化SDL系统。此函数用于初始化SDL库，参数 `SDL_INIT_VIDEO` 表示初始化视频子系统。

2. `SDL_CreateWindow("Simplest Video Play SDL2", SDL_WINDOWPOS_UNDEFINED, SDL_WINDOWPOS_UNDEFINED, screen_w, screen_h, SDL_WINDOW_OPENGL | SDL_WINDOW_RESIZABLE)`: 创建窗口SDL_Window。该函数用于创建一个窗口，参数包括窗口标题、位置和大小，以及窗口的属性。

3. `SDL_CreateRenderer(screen, -1, 0)`: 创建渲染器SDL_Renderer。该函数用于创建一个渲染器，将渲染器与特定的窗口关联，参数包括要绑定的窗口和渲染器的索引。

4. `SDL_CreateTexture(sdlRenderer, pixformat, SDL_TEXTUREACCESS_STREAMING, pixel_w, pixel_h)`: 创建纹理SDL_Texture。该函数用于创建一个纹理，纹理是一个用于存储图像数据的对象，参数包括要绑定的渲染器、像素格式、访问方式以及纹理的宽度和高度。

5. `SDL_UpdateTexture(sdlTexture, NULL, buffer, pixel_w)`: 设置纹理的数据。该函数用于更新纹理的图像数据，参数包括要更新的纹理、更新的区域（NULL表示整个纹理）、图像数据的来源缓冲区以及图像数据的宽度。

6. `SDL_RenderCopy(sdlRenderer, sdlTexture, NULL, &sdlRect)`: 将纹理的数据拷贝给渲染器。该函数用于将纹理的图像数据渲染到指定的渲染器上，参数包括源纹理、源区域（NULL表示整个纹理）、目标区域（即屏幕上的位置和大小）。

7. `SDL_RenderPresent(sdlRenderer)`: 显示。该函数用于将渲染器上的所有绘制操作呈现到屏幕上，使得用户可以看到绘制的图像。

8. `SDL_Delay(40)`: 工具函数，用于延时。该函数用于暂停程序的执行一段时间，参数表示要延时的毫秒数。

9. `SDL_Quit()`: 退出SDL系统。该函数用于释放SDL库所占用的资源，并退出SDL系统，程序执行到此结束。

这些函数组合在一起实现了一个简单的视频播放器，能够打开窗口并播放YUV格式的视频文件。



> **注**
>
> - 纹理
>
>   在SDL中，纹理（Texture）是用于在屏幕上渲染图像的对象。SDL提供了一套用于创建、加载、操作和渲染纹理的函数，使得开发者可以方便地在应用程序中展示图像、动画和其他视觉元素。
>
>   SDL中的纹理主要通过以下几个函数来创建和操作：
>
>   1. **SDL_CreateTexture()**: 用于创建一个新的纹理对象。开发者可以指定纹理的宽度、高度、像素格式等属性，并将图像数据加载到纹理中。
>   2. **SDL_UpdateTexture()**: 用于更新纹理的像素数据。开发者可以将新的图像数据拷贝到已创建的纹理中，以实现动态更新纹理的效果。
>   3. **SDL_RenderCopy()**: 用于将纹理的数据拷贝到渲染器中进行显示。开发者可以指定纹理的位置、大小等参数，将纹理渲染到屏幕上指定的位置。
>   4. **SDL_DestroyTexture()**: 用于销毁一个已创建的纹理对象，释放相关的资源。
>
>   SDL中的纹理通常是与SDL_Renderer相关联的，即在创建纹理时需要指定一个SDL_Renderer对象。渲染器负责将纹理渲染到屏幕上，开发者通过渲染器来管理和操作纹理的显示。
>
>   SDL中的纹理是一种用于在屏幕上渲染图像的对象，通过SDL提供的函数，开发者可以方便地创建、加载、操作和渲染纹理，实现图像的显示和动画效果。
>
> - SDL_Rect
>
>   在SDL中，SDL_Rect是一个用于表示矩形区域的结构体，其定义如下：
>
>   ```c
>   typedef struct {
>       int x, y; // 矩形左上角的坐标
>       int w, h; // 矩形的宽度和高度
>   } SDL_Rect;
>   ```
>
>   SDL_Rect结构体包含了矩形区域的左上角的坐标（x、y）以及矩形的宽度（w）和高度（h）。通过这些信息，可以准确地定义一个矩形的区域。
>
>   SDL_Rect结构体通常用于指定屏幕上的图像或纹理的位置和大小。例如，在渲染图像或纹理时，可以通过SDL_Rect来指定图像或纹理在屏幕上的位置和大小，以确定其在屏幕上的显示区域。
>
>   SDL_Rect结构体的成员变量及其含义如下：
>
>   - **x**: 表示矩形左上角的横坐标。
>   - **y**: 表示矩形左上角的纵坐标。
>   - **w**: 表示矩形的宽度。
>   - **h**: 表示矩形的高度。
>
>   通过使用SDL_Rect结构体，开发者可以方便地对矩形区域进行描述和操作，从而实现图像或纹理在屏幕上的精确显示和布局。




## FFmpeg开发用

### 转码h264与yuv测试
### 

```cpp
#define _CRT_SECURE_NO_WARNINGS
#include <iostream>

// 引入FFmpeg库头文件
extern "C"
{
#include "libavcodec/avcodec.h"
#include "libavformat/avformat.h"
#include "libswscale/swscale.h"
#include "libavdevice/avdevice.h"
#include "libavutil/imgutils.h"
}

int main(int argc, char* argv[]) {
	// 声明FFmpeg相关变量
	AVFormatContext* pFormatCtx = NULL;
	int i, videoindex;
	AVCodecContext* pCodecCtx = NULL;
	const AVCodec* pCodec = NULL;
	AVFrame* pFrame = NULL, * pFrameYUV = NULL;
	uint8_t* out_buffer = NULL;
	AVPacket* packet = NULL;
	int ret, got_picture;
	struct SwsContext* img_convert_ctx = NULL;
	// 视频文件路径
	char filepath[] = "output.mp4";
	int frame_cnt;

	// 分配AVFormatContext结构
	pFormatCtx = avformat_alloc_context();

	// 打开输入文件
	if (avformat_open_input(&pFormatCtx, filepath, NULL, NULL) != 0) {
		printf("Couldn't open input stream.\n");
		return -1;
	}
	// 查找流信息
	if (avformat_find_stream_info(pFormatCtx, NULL) < 0) {
		printf("Couldn't find stream information.\n");
		return -1;
	}

	// 获取视频流的索引
	videoindex = av_find_best_stream(pFormatCtx, AVMEDIA_TYPE_VIDEO, -1, -1, NULL, 0);
	/*for (i = 0; i < pFormatCtx->nb_streams; i++)
		if (pFormatCtx->streams[i]->codecpar->codec_type == AVMEDIA_TYPE_VIDEO) {
			videoindex = i;
			break;
		}*/
	if (videoindex == -1) {
		printf("Didn't find a video stream.\n");
		return -1;
	}

	// 分配AVCodecContext结构并填充参数
	pCodecCtx = avcodec_alloc_context3(NULL);
	avcodec_parameters_to_context(pCodecCtx, pFormatCtx->streams[videoindex]->codecpar);
	// 查找解码器
	pCodec = avcodec_find_decoder(pCodecCtx->codec_id);

	if (pCodec == NULL) {
		printf("Codec not found.\n");
		return -1;
	}
	// 打开解码器
	if (avcodec_open2(pCodecCtx, pCodec, NULL) < 0) {
		printf("Could not open codec.\n");
		return -1;
	}
    /*
	// 打印编解码器信息
	const AVCodecDescriptor* desc = avcodec_descriptor_get(pCodecCtx->codec_id);
	if (desc) {
		printf("编解码器名称: %s\n", desc->name);
	}
	else {
		printf("未找到编解码器\n");
	}
	printf("时长：%lld\n", pFormatCtx->duration);
	printf("封装格式：%s\n", pFormatCtx->iformat->name);
	printf("封装格式：%s\n", pFormatCtx->iformat->long_name);
	printf("视频编码器：%s\n", avcodec_get_name(pFormatCtx->streams[0]->codecpar->codec_id));
	printf("音频编码器：%s\n", avcodec_get_name(pFormatCtx->streams[1]->codecpar->codec_id));
	printf("视频编码器：%d\n", pFormatCtx->streams[0]->codecpar->codec_id);
	printf("音频编码器：%d\n", pFormatCtx->streams[1]->codecpar->codec_id);

	printf("宽：%d*%d\n", pFormatCtx->streams[0]->codecpar->width, pFormatCtx->streams[0]->codecpar->height);*/

	// 分配AVFrame结构
	pFrame = av_frame_alloc();
	pFrameYUV = av_frame_alloc();
/*
av_malloc(size_t size) 函数：
参数：
size：要分配的内存大小，以字节为单位。

作用：分配指定大小的内存块，并返回指向该内存块的指针。内存的内容是未初始化的。

av_image_get_buffer_size(enum AVPixelFormat pix_fmt, int width, int height, int align) 函数：
参数：
pix_fmt：图像的像素格式，即采样格式，例如 AV_PIX_FMT_YUV420P。
width：图像的宽度（以像素为单位）。
height：图像的高度（以像素为单位）。
align：内存对齐的要求，通常设置为 1。

作用：根据给定的像素格式、宽度和高度，计算并返回存储图像数据所需的缓冲区大小，单位为字节。

av_image_fill_arrays(uint8_t *dst_data[4], int dst_linesize[4], const uint8_t *src, enum AVPixelFormat pix_fmt, int width, int height, int align) 函数：
参数：
dst_data：指向包含图像数据的指针数组。通常情况下，这是一个 uint8_t* 类型的数组，有四个元素，用于存储 Y、U、V 平面的指针以及 alpha 通道（如果有）的指针。
dst_linesize：指向包含图像每行数据大小的数组。通常情况下，这是一个 int 类型的数组，有四个元素，分别对应 Y、U、V 平面以及 alpha 通道（如果有）的每行数据大小。
src：指向源图像数据的指针，通常是一块连续的内存区域。
pix_fmt：源图像的像素格式。
width：图像的宽度（以像素为单位）。
height：图像的高度（以像素为单位）。
align：内存对齐的要求，通常设置为 1。 注："align" 是用于内存对齐的参数。内存对齐是指将数据存储在内存中时，按照某种规则将数据的起始地址对齐到特定的边界。在这里，align 参数表示要求数据在内存中的对齐方式，通常设置为 1 表示不需要额外的对齐。如果设置为其他值，比如 16 或者 32，表示要求数据按照这个值的倍数对齐。

作用：填充目标图像数据指针数组和行大小数组，以便将图像数据存储到指定的内存中。同时，该函数也会设置 AVFrame 结构体的相关属性，例如像素格式、宽度、高度等。
*/
	// 分配YUV输出缓冲区
	out_buffer = (uint8_t*)av_malloc(av_image_get_buffer_size(AV_PIX_FMT_YUV420P, pCodecCtx->width, pCodecCtx->height, 1));
	av_image_fill_arrays(pFrameYUV->data, pFrameYUV->linesize, out_buffer, AV_PIX_FMT_YUV420P, pCodecCtx->width, pCodecCtx->height, 1);
	// 分配AVPacket结构
	packet = (AVPacket*)av_malloc(sizeof(AVPacket));
	// 打印文件信息
	printf("--------------- File Information ----------------\n");
	av_dump_format(pFormatCtx, 0, filepath, 0);
	printf("-------------------------------------------------\n");
	// 初始化图像转换上下文
	img_convert_ctx = sws_getContext(pCodecCtx->width, pCodecCtx->height, pCodecCtx->pix_fmt,
		pCodecCtx->width, pCodecCtx->height, AV_PIX_FMT_YUV420P, SWS_BICUBIC, NULL, NULL, NULL);

	// 打开H264和YUV文件
	FILE* fp_264 = fopen("test264.h264", "wb+");
	FILE* fp_yuv = fopen("testyuv.yuv", "wb+");

	// 初始化帧计数器
	frame_cnt = 0;
	// 循环读取每一帧数据
	while (av_read_frame(pFormatCtx, packet) >= 0) {
		// 检查当前数据包是否为视频流
		if (packet->stream_index == videoindex) {
			// 将数据包中的数据写入H264文件中
			fwrite(packet->data, 1, packet->size, fp_264);
			// 发送数据包进行解码
			ret = avcodec_send_packet(pCodecCtx, packet);
			if (ret < 0) {
				printf("Decode Error.\n");
				return -1;
			}
			// 循环接收解码后的视频帧
			while (ret >= 0) {
				ret = avcodec_receive_frame(pCodecCtx, pFrame);
				if (ret == AVERROR(EAGAIN) || ret == AVERROR_EOF)
					break;
				else if (ret < 0) {
					printf("Error during decoding.\n");
					return -1;
				}
				// 判断是否成功获取一帧图像
				if (ret >= 0) {
					// 将解码后的帧转换为YUV格式
					sws_scale(img_convert_ctx, (const uint8_t* const*)pFrame->data, pFrame->linesize, 0, pCodecCtx->height,
						pFrameYUV->data, pFrameYUV->linesize);
/*
int sws_scale(struct SwsContext *c, const uint8_t *const srcSlice[],
              const int srcStride[], int srcSliceY, int srcSliceH,
              uint8_t *const dst[], const int dstStride[]);
参数说明如下：

c：sws_getContext() 返回的 SwsContext 上下文。
srcSlice：源图像数据的指针数组，每个元素指向源图像的一个图像平面。
srcStride：源图像每个图像平面的行大小数组。
srcSliceY：源图像的起始行。
srcSliceH：源图像的高度。
dst：目标图像数据的指针数组，每个元素指向目标图像的一个图像平面。
dstStride：目标图像每个图像平面的行大小数组。
该函数返回一个整型值，表示成功转换的行数，或者一个负值表示出错。

sws_scale() 函数将源图像数据转换为目标图像数据，根据指定的 SwsContext 上下文和参数执行图像转换和缩放操作。它将源图像数据逐行地转换为目标图像数据，并根据需要进行缩放。输出的目标图像数据存储在 dst 参数指向的内存中。

这个函数通常在进行视频编码、解码以及视频处理等场景中被广泛使用，用于将图像数据从一种格式或分辨率转换为另一种格式或分辨率。              
*/       
					// 输出解码的帧索引
					printf("Decoded frame index: %d\n", frame_cnt);
					// 将YUV数据写入YUV文件中
					fwrite(pFrameYUV->data[0], 1, pCodecCtx->width* pCodecCtx->height, fp_yuv);
					fwrite(pFrameYUV->data[1], 1, pCodecCtx->width* pCodecCtx->height / 4, fp_yuv);
					fwrite(pFrameYUV->data[2], 1, pCodecCtx->width* pCodecCtx->height / 4, fp_yuv);
					frame_cnt++;
				}
			}
		}
		// 释放数据包引用的资源，包括packet->data
		av_packet_unref(packet);
	}

	// 关闭文件和释放内存
	fclose(fp_264);
	fclose(fp_yuv);
	sws_freeContext(img_convert_ctx);
	av_packet_free(&packet);
	av_frame_free(&pFrameYUV);
	av_frame_free(&pFrame);
	avcodec_close(pCodecCtx);
	avformat_close_input(&pFormatCtx);
    return 0;
}
```



### SDL播放YUV测试

```cpp
#include <stdio.h> // 包含标准输入输出头文件
#include <SDL.h> // 包含SDL库头文件

const int bpp=12; // 像素位深度，每个像素占用的位数

int screen_w=960,screen_h=540; // 屏幕宽度和高度
const int pixel_w=1920,pixel_h=1080; // 像素宽度和高度

unsigned char buffer[pixel_w*pixel_h*bpp/8]; // 存储像素数据的缓冲区

// 刷新事件
#define REFRESH_EVENT  (SDL_USEREVENT + 1)
// 中断事件
#define BREAK_EVENT  (SDL_USEREVENT + 2)

int thread_exit=0; // 线程退出时非0

// 视频刷新函数
int refresh_video(void *opaque){
    thread_exit=0; // 初始化线程退出标志
    while (thread_exit==0) { // 当线程未退出时循环执行
        SDL_Event event; // 创建SDL事件
        event.type = REFRESH_EVENT; // 设置事件类型为刷新事件
        SDL_PushEvent(&event); // 将事件压入事件队列
        SDL_Delay(40); // 延迟40毫秒
    }
    thread_exit=0; // 重置线程退出标志
    // 发送中断事件
    SDL_Event event;
    event.type = BREAK_EVENT;
    SDL_PushEvent(&event);
    return 0;
}

int main(int argc, char* argv[])
{
    if(SDL_Init(SDL_INIT_VIDEO)) { // 初始化SDL视频模块，如果失败则输出错误信息
        printf( "Could not initialize SDL - %s\n", SDL_GetError());
        return -1;
    }

    SDL_Window *screen; // 创建SDL窗口指针
    // SDL 2.0支持多窗口，创建窗口并指定窗口标题、位置、大小、可选参数
    screen = SDL_CreateWindow("Simplest Video Play SDL2", SDL_WINDOWPOS_UNDEFINED, SDL_WINDOWPOS_UNDEFINED,
        screen_w, screen_h,SDL_WINDOW_OPENGL|SDL_WINDOW_RESIZABLE);
    if(!screen) { // 如果创建窗口失败则输出错误信息
        printf("SDL: could not create window - exiting:%s\n",SDL_GetError());
        return -1;
    }
    // 创建SDL渲染器
    SDL_Renderer* sdlRenderer = SDL_CreateRenderer(screen, -1, 0);

    Uint32 pixformat=0; // 像素格式
    // YUV像素格式，IYUV: Y + U + V  (3个平面)
    pixformat= SDL_PIXELFORMAT_IYUV;

    // 创建SDL纹理
    SDL_Texture* sdlTexture = SDL_CreateTexture(sdlRenderer,pixformat, SDL_TEXTUREACCESS_STREAMING,pixel_w,pixel_h);

    FILE *fp=NULL; // 文件指针初始化
    // 以二进制读写方式打开文件
    fp=fopen("testyuv.yuv","rb+");

    if(fp==NULL){ // 如果文件打开失败则输出错误信息
        printf("cannot open this file\n");
        return -1;
    }

    SDL_Rect sdlRect; // SDL矩形

    // 创建刷新线程
    SDL_Thread *refresh_thread = SDL_CreateThread(refresh_video,NULL,NULL);
    SDL_Event event; // SDL事件
    while(1){
        // 等待事件
        SDL_WaitEvent(&event);
        if(event.type==REFRESH_EVENT){ // 如果事件类型为刷新事件
            if (fread(buffer, 1, pixel_w*pixel_h*bpp/8, fp) != pixel_w*pixel_h*bpp/8){ // 读取文件数据到缓冲区
                // 循环读取文件数据
                fseek(fp, 0, SEEK_SET);
                fread(buffer, 1, pixel_w*pixel_h*bpp/8, fp);
            }

            // 更新纹理
            SDL_UpdateTexture( sdlTexture, NULL, buffer, pixel_w);

            /*黑边效果*/
            /*
            sdlRect.x = 10;
        	sdlRect.y = 10;
	        sdlRect.w = screen_w - 20;
	        sdlRect.h = screen_h - 20;
            */
            // 修正窗口大小变化
            sdlRect.x = 0;
            sdlRect.y = 0;
            sdlRect.w = screen_w;
            sdlRect.h = screen_h;

            // 渲染并显示
            SDL_RenderClear( sdlRenderer );
            SDL_RenderCopy( sdlRenderer, sdlTexture, NULL, &sdlRect);
            SDL_RenderPresent( sdlRenderer );

        }else if(event.type==SDL_WINDOWEVENT){ // 如果事件类型为窗口事件
            // 处理窗口大小变化
            SDL_GetWindowSize(screen,&screen_w,&screen_h);
        }else if(event.type==SDL_QUIT){ // 如果事件类型为退出事件
            thread_exit=1; // 设置线程退出标志
        }else if(event.type==BREAK_EVENT){ // 如果事件类型为中断事件
            break; // 退出循环
        }
    }
    SDL_Quit(); // 退出SDL
    return 0; // 返回0表示成功执行
}
```



### 简易视频播放器

```cpp
// FFSDLScreen.cpp : 此文件包含 "main" 函数。程序执行将在此处开始并结束。
//
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h> // 包含标准输入输出头文件

extern "C"
{
#include "libavcodec/avcodec.h"
#include "libavformat/avformat.h"
#include "libswscale/swscale.h"
#include "libavdevice/avdevice.h"
#include "libavutil/imgutils.h"
#include "sdl/SDL.h"
}


const int bpp = 12; // 像素位深度，每个像素占用的位数


// 刷新事件
#define REFRESH_EVENT  (SDL_USEREVENT + 1)
// 中断事件
#define BREAK_EVENT  (SDL_USEREVENT + 2)

int paused = 0; // 非0是视频暂停
int thread_exit = 0; // 非0时线程退出
int video_exit = 0; // 非0时视频退出

// 视频刷新函数
int refresh_video(void* opaque) {
	thread_exit = 0; // 初始化线程退出标志
	while (thread_exit == 0) { // 当线程未退出时循环执行
		SDL_Event event; // 创建SDL事件
		event.type = REFRESH_EVENT; // 设置事件类型为刷新事件
		SDL_PushEvent(&event); // 将事件压入事件队列
		SDL_Delay(40); // 延迟40毫秒
		while (paused && thread_exit == 0) SDL_Delay(100);
	}
	thread_exit = 0; // 重置线程退出标志
	// 发送中断事件
	SDL_Event event;
	event.type = BREAK_EVENT;
	SDL_PushEvent(&event);
	return 0;
}


int main(int argc, char* argv[])
{
	if (argc != 2) {
		printf("error parameters!\n");
		return 0;
	}

	AVFormatContext* pFormatCtx = NULL;
	int				i, videoindex;
	AVCodecContext* pCodecCtx = NULL;
	const AVCodec* pCodec = NULL;
	AVFrame* pFrame = NULL, * pFrameYUV = NULL;
	uint8_t* out_buffer = NULL;
	AVPacket* packet = NULL;
	int y_size;
	int ret, got_picture;
	struct SwsContext* img_convert_ctx = NULL;
	SDL_Rect sdlRect; // SDL矩形
	char* filepath = (char*)malloc(strlen(argv[1]) + 1);
	if (filepath == NULL) {
		printf("Memory allocation failed!\n");
		return 0;
	}
	strcpy(filepath, argv[1]);//输入文件路径
	int frame_cnt; // 帧数据


	pFormatCtx = avformat_alloc_context();

	if (avformat_open_input(&pFormatCtx, filepath, NULL, NULL) != 0) {
		printf("Couldn't open input stream.\n");
		return -1;
	}
	if (avformat_find_stream_info(pFormatCtx, NULL) < 0) {
		printf("Couldn't find stream information.\n");
		return -1;
	}
	videoindex = av_find_best_stream(pFormatCtx, AVMEDIA_TYPE_VIDEO, -1, -1, NULL, 0);
	if (videoindex == -1) {
		printf("Didn't find a video stream.\n");
		return -1;
	}

	pCodecCtx = avcodec_alloc_context3(NULL);
	avcodec_parameters_to_context(pCodecCtx, pFormatCtx->streams[videoindex]->codecpar);
	pCodec = avcodec_find_decoder(pCodecCtx->codec_id);

	if (pCodec == NULL) {
		printf("Codec not found.\n");
		return -1;
	}
	if (avcodec_open2(pCodecCtx, pCodec, NULL) < 0) {
		printf("Could not open codec.\n");
		return -1;
	}


	pFrame = av_frame_alloc();
	pFrameYUV = av_frame_alloc();
	out_buffer = (uint8_t*)av_malloc(av_image_get_buffer_size(AV_PIX_FMT_YUV420P, pCodecCtx->width, pCodecCtx->height, 1));
	av_image_fill_arrays(pFrameYUV->data, pFrameYUV->linesize, out_buffer, AV_PIX_FMT_YUV420P, pCodecCtx->width, pCodecCtx->height, 1);
	packet = (AVPacket*)av_malloc(sizeof(AVPacket));
	//Output Info-----------------------------
	printf("--------------- File Information ----------------\n");
	av_dump_format(pFormatCtx, 0, filepath, 0);
	printf("-------------------------------------------------\n");
	img_convert_ctx = sws_getContext(pCodecCtx->width, pCodecCtx->height, pCodecCtx->pix_fmt,
		pCodecCtx->width, pCodecCtx->height, AV_PIX_FMT_YUV420P, SWS_BICUBIC, NULL, NULL, NULL);


	// 创建刷新线程
	SDL_Thread* refresh_thread = SDL_CreateThread(refresh_video, NULL, NULL);
	SDL_Event event; // SDL事件
	const int pixel_w = pCodecCtx->width, pixel_h = pCodecCtx->height; // 像素宽度和高度
	int screen_w = pixel_w / 2, screen_h = pixel_h / 2; // 屏幕宽度和高度

	if (SDL_Init(SDL_INIT_VIDEO)) { // 初始化SDL视频模块，如果失败则输出错误信息
		printf("Could not initialize SDL - %s\n", SDL_GetError());
		return -1;
	}

	SDL_Window* screen; // 创建SDL窗口指针
	// SDL 2.0支持多窗口，创建窗口并指定窗口标题、位置、大小、可选参数
	screen = SDL_CreateWindow("Simplest Video Play SDL2", SDL_WINDOWPOS_UNDEFINED, SDL_WINDOWPOS_UNDEFINED,
		screen_w, screen_h, SDL_WINDOW_OPENGL | SDL_WINDOW_RESIZABLE);
	if (!screen) { // 如果创建窗口失败则输出错误信息
		printf("SDL: could not create window - exiting:%s\n", SDL_GetError());
		return -1;
	}
	// 创建SDL渲染器
	SDL_Renderer* sdlRenderer = SDL_CreateRenderer(screen, -1, 0);

	Uint32 pixformat = 0; // 像素格式
	// YUV像素格式，IYUV: Y + U + V  (3个平面)
	pixformat = SDL_PIXELFORMAT_IYUV;

	// 创建SDL纹理
	SDL_Texture* sdlTexture = SDL_CreateTexture(sdlRenderer, pixformat, SDL_TEXTUREACCESS_STREAMING, pixel_w, pixel_h);

	frame_cnt = 0;
	while (av_read_frame(pFormatCtx, packet) >= 0 && !video_exit) {
		if (packet->stream_index == videoindex) {
			ret = avcodec_send_packet(pCodecCtx, packet);
			if (ret < 0) {
				printf("Decode Error.\n");
				return -1;
			}
			while (ret >= 0) {
				ret = avcodec_receive_frame(pCodecCtx, pFrame);
				if (ret == AVERROR(EAGAIN) || ret == AVERROR_EOF)
					break;
				else if (ret < 0) {
					printf("Error during decoding.\n");
					return -1;
				}
				SDL_WaitEvent(&event);
				if (event.type == REFRESH_EVENT) { // 如果事件类型为刷新事件

					sws_scale(img_convert_ctx, (const uint8_t* const*)pFrame->data, pFrame->linesize, 0, pCodecCtx->height,
						pFrameYUV->data, pFrameYUV->linesize);
					printf("Decoded frame index: %d\n", frame_cnt);
					// 更新纹理
					SDL_UpdateTexture(sdlTexture, NULL, pFrameYUV->data[0], pFrameYUV->linesize[0]);

					// 修正窗口大小变化
					sdlRect.x = 0;
					sdlRect.y = 0;
					sdlRect.w = screen_w;
					sdlRect.h = screen_h;

					// 渲染并显示
					SDL_RenderClear(sdlRenderer);
					SDL_RenderCopy(sdlRenderer, sdlTexture, NULL, &sdlRect);
					SDL_RenderPresent(sdlRenderer);
					frame_cnt++;
				}
				else if (event.type == SDL_WINDOWEVENT) { // 如果事件类型为窗口事件
					// 处理窗口大小变化
					SDL_GetWindowSize(screen, &screen_w, &screen_h);
				}
				else if(event.type == SDL_KEYDOWN && event.key.keysym.sym == SDLK_SPACE) {
					paused = ~paused;
				}
				else if (event.type == SDL_QUIT) { // 如果事件类型为退出事件
					thread_exit = 1; // 设置线程退出标志
				}
				else if (event.type == BREAK_EVENT) { // 如果事件类型为中断事件
					video_exit = 1;
					break; // 退出循环
				}
			}
		}
		av_packet_unref(packet);
	}
	SDL_Quit();
	sws_freeContext(img_convert_ctx);
	av_packet_free(&packet);
	av_frame_free(&pFrameYUV);
	av_frame_free(&pFrame);
	avcodec_close(pCodecCtx);
	avformat_close_input(&pFormatCtx);


	return 0;
}

```





### 简易音视频播放器

```cpp
#define _CRT_SECURE_NO_WARNINGS
#include <iostream>
#include <thread>

extern "C"
{
#include "libavcodec/avcodec.h"
#include "libavformat/avformat.h"
#include "libswscale/swscale.h"
#include "libswresample/swresample.h"
#include "libavdevice/avdevice.h"
#include "libavutil/imgutils.h"
#include "libavutil/audio_fifo.h"
#include "sdl/SDL.h"
}

#undef main
AVAudioFifo* fifo = NULL;
SDL_AudioSpec wanted_spec, spec;
SDL_mutex* mtx = NULL;
// 刷新事件
#define REFRESH_EVENT  (SDL_USEREVENT + 1)
// 中断事件
#define BREAK_EVENT  (SDL_USEREVENT + 2)



const int bpp = 12; // 像素位深度，每个像素占用的位数


int paused = 0; // 非0是视频暂停
int thread_exit = 0; // 非0时线程退出
int video_exit = 0; // 非0时视频退出

AVFormatContext* pFormatCtx = NULL;
int				videoIndex, audioIndex;
AVCodecContext* pVideoCodecCtx = NULL, * pAudioCodecCtx = NULL;
const AVCodec* pVideoCodec = NULL;
const AVCodec* pAudioCodec = NULL;
AVFrame* pVideoFrame = NULL, * pYUVFrame = NULL, * pAudioFrame = NULL;
enum AVSampleFormat forceFormat;
uint8_t* outBuffer = NULL;
AVPacket* packet = NULL;
AVDictionary* opts = NULL;
int ret, audioId;
struct SwsContext* imgConvertCtx = NULL;
struct SwrContext* swr_ctx = NULL;
SDL_Rect sdlRect; // SDL矩形
SDL_Thread* refresh_thread = NULL;
SDL_Renderer* sdlRenderer = NULL;
SDL_Texture* sdlTexture = NULL;
Uint32 pixformat;
int pixel_w, pixel_h; // 像素宽度和高度
int screen_w, screen_h; // 屏幕宽度和高度
int videoFrameCnt, audioFrameCnt; // 帧数据

// 视频刷新函数
int refresh_video(void* opaque) {
	thread_exit = 0; // 初始化线程退出标志
	while (thread_exit == 0) { // 当线程未退出时循环执行
		SDL_Event event; // 创建SDL事件
		event.type = REFRESH_EVENT; // 设置事件类型为刷新事件
		SDL_PushEvent(&event); // 将事件压入事件队列
		SDL_Delay(40); // 延迟40毫秒
		while (paused && thread_exit == 0) SDL_Delay(100);
	}
	thread_exit = 0; // 重置线程退出标志
	// 发送中断事件
	SDL_Event event;
	event.type = BREAK_EVENT;
	SDL_PushEvent(&event);
	return 0;
}

//音频回调函数
void audioCallBack(void* userdata, Uint8* stream, int len) {
	//由于AVAudioFifo非线程安全，且是子线程触发此回调，所以需要加锁
	SDL_LockMutex(mtx);
	//读取队列中的音频数据
	av_audio_fifo_read(fifo, (void**)&stream, spec.samples);
	SDL_UnlockMutex(mtx);
}



int main(int argc, char* argv[])
{
	if (argc != 2) {
		printf("error parameters!\n");
		return 0;
	}

	char* filepath = (char*)malloc(strlen(argv[1]) + 1);
	if (filepath == NULL) {
		printf("Memory allocation failed!\n");
		return 0;
	}
	strcpy(filepath, argv[1]);//输入文件路径

	//使用多线程解码
	if (!av_dict_get(opts, "threads", NULL, 0))
		av_dict_set(&opts, "threads", "auto", 0);

	// 获取封装格式信息
	pFormatCtx = avformat_alloc_context();

	if (avformat_open_input(&pFormatCtx, filepath, NULL, NULL) != 0) {
		printf("Couldn't open input stream.\n");
		goto end;
	}
	if (avformat_find_stream_info(pFormatCtx, NULL) < 0) {
		printf("Couldn't find stream information.\n");
		goto end;
	}

	// 获取视频解码器及解码数据
	videoIndex = av_find_best_stream(pFormatCtx, AVMEDIA_TYPE_VIDEO, -1, -1, NULL, 0);
	if (videoIndex == -1) {
		printf("Didn't find a video stream.\n");
		goto end;
	}

	pVideoCodecCtx = avcodec_alloc_context3(NULL);
	avcodec_parameters_to_context(pVideoCodecCtx, pFormatCtx->streams[videoIndex]->codecpar);
	pVideoCodec = avcodec_find_decoder(pVideoCodecCtx->codec_id);
	if (pVideoCodec == NULL) {
		printf("Video codec not found.\n");
		goto end;
	}
	if (avcodec_open2(pVideoCodecCtx, pVideoCodec, &opts) < 0) {
		printf("Could not open video codec.\n");
		goto end;
	}


	// 获取音频解码器及解码数据
	audioIndex = av_find_best_stream(pFormatCtx, AVMEDIA_TYPE_AUDIO, -1, -1, NULL, 0);
	if (audioIndex == -1) {
		printf("Didn't find a audio stream.\n");
		goto end;
	}

	pAudioCodecCtx = avcodec_alloc_context3(NULL);
	avcodec_parameters_to_context(pAudioCodecCtx, pFormatCtx->streams[audioIndex]->codecpar);
	pAudioCodec = avcodec_find_decoder(pAudioCodecCtx->codec_id);
	if (pAudioCodec == NULL) {
		printf("Audio codec not found.\n");
		goto end;
	}
	if (avcodec_open2(pAudioCodecCtx, pAudioCodec, &opts) < 0) {
		printf("Could not open audio codec.\n");
		goto end;
	}

	
	// 视频帧初始化
	pVideoFrame = av_frame_alloc();
	pYUVFrame = av_frame_alloc();
	pAudioFrame = av_frame_alloc();
	outBuffer = (uint8_t*)av_malloc(av_image_get_buffer_size(AV_PIX_FMT_YUV420P, pVideoCodecCtx->width, pVideoCodecCtx->height, 1));
	av_image_fill_arrays(pYUVFrame->data, pYUVFrame->linesize, outBuffer, AV_PIX_FMT_YUV420P, pVideoCodecCtx->width, pVideoCodecCtx->height, 1);
	packet = (AVPacket*)av_malloc(sizeof(AVPacket));
	//打印信息-----------------------------
	printf("--------------- File Information ----------------\n");
	av_dump_format(pFormatCtx, 0, filepath, 0);
	printf("-------------------------------------------------\n");
	imgConvertCtx = sws_getContext(pVideoCodecCtx->width, pVideoCodecCtx->height, pVideoCodecCtx->pix_fmt,
		pVideoCodecCtx->width, pVideoCodecCtx->height, AV_PIX_FMT_YUV420P, SWS_BICUBIC, NULL, NULL, NULL);


	// 创建视频刷新线程
	refresh_thread = SDL_CreateThread(refresh_video, NULL, NULL);
	SDL_Event event; // SDL事件
	pixel_w = pVideoCodecCtx->width, pixel_h = pVideoCodecCtx->height; // 像素宽度和高度
	screen_w = pixel_w / 2, screen_h = pixel_h / 2; // 屏幕宽度和高度

	if (SDL_Init(SDL_INIT_VIDEO | SDL_INIT_AUDIO)) { // 初始化SDL视频模块，如果失败则输出错误信息
		printf("Could not initialize SDL - %s\n", SDL_GetError());
		goto end;
	}

	SDL_Window* screen; // 创建SDL窗口指针
	// SDL 2.0支持多窗口，创建窗口并指定窗口标题、位置、大小、可选参数
	screen = SDL_CreateWindow(filepath, SDL_WINDOWPOS_UNDEFINED, SDL_WINDOWPOS_UNDEFINED,
		screen_w, screen_h, SDL_WINDOW_OPENGL | SDL_WINDOW_RESIZABLE);
	if (!screen) { // 如果创建窗口失败则输出错误信息
		printf("SDL: could not create window - exiting:%s\n", SDL_GetError());
		goto end;
	}
	// 创建SDL渲染器
	sdlRenderer = SDL_CreateRenderer(screen, -1, 0);

	pixformat = 0; // 像素格式
	// YUV像素格式，IYUV: Y + U + V  (3个平面)
	pixformat = SDL_PIXELFORMAT_IYUV;

	// 创建SDL纹理
	sdlTexture = SDL_CreateTexture(sdlRenderer, pixformat, SDL_TEXTUREACCESS_STREAMING, pixel_w, pixel_h);


	// 设置SDL音频参数
	wanted_spec.freq = pAudioCodecCtx->sample_rate;
	wanted_spec.format = AUDIO_F32SYS;
	wanted_spec.channels = pAudioCodecCtx->ch_layout.nb_channels;
	wanted_spec.silence = 0;
	wanted_spec.samples = FFMAX(512, 2 << av_log2(wanted_spec.freq / 30));;
	wanted_spec.callback = audioCallBack;
	wanted_spec.userdata = NULL;
	audioId = SDL_OpenAudioDevice(NULL, 0, &wanted_spec, &spec, 1);
	if (audioId < 2) {
		printf("SDL_OpenAudioDeviceError:%s\n.", SDL_GetError());
		goto end;
	}

	switch (spec.format)
	{
	case	AUDIO_S16SYS:
		forceFormat = AV_SAMPLE_FMT_S16;
		break;
	case	AUDIO_S32SYS:
		forceFormat = AV_SAMPLE_FMT_S32;
		break;
	case	AUDIO_F32SYS:
		forceFormat = AV_SAMPLE_FMT_FLT;
		break;
	default:
		printf("audio device format was not surported!\n");
		goto end;
		break;
	}


	//使用音频队列
	fifo = av_audio_fifo_alloc(forceFormat, spec.channels, spec.samples * 10);
	if (!fifo)
	{
		printf("alloc fifo failed!\n");
		goto end;
	}
	mtx = SDL_CreateMutex();
	if (!mtx)
	{
		printf("alloc mutex failed!\n");
		goto end;
	}
	SDL_PauseAudioDevice(audioId, 0);


	videoFrameCnt = 0;
	audioFrameCnt = 0;
	while (av_read_frame(pFormatCtx, packet) >= 0 && !video_exit) {
		if (packet->stream_index == videoIndex) {
			ret = avcodec_send_packet(pVideoCodecCtx, packet);
			if (ret < 0) {
				printf("Video decode error.\n");
				goto end;
			}
			while (ret >= 0) {
				ret = avcodec_receive_frame(pVideoCodecCtx, pVideoFrame);
				if (ret == AVERROR(EAGAIN) || ret == AVERROR_EOF)
					break;
				else if (ret < 0) {
					printf("Error during video decoding.\n");
					goto end;
				}
				SDL_WaitEvent(&event);
				if (event.type == REFRESH_EVENT) { // 如果事件类型为刷新事件

					sws_scale(imgConvertCtx, (const uint8_t* const*)pVideoFrame->data, pVideoFrame->linesize, 0, pVideoCodecCtx->height,
						pYUVFrame->data, pYUVFrame->linesize);
					printf("Decoded video frame index: %d\n", videoFrameCnt);
					// 更新纹理
					SDL_UpdateTexture(sdlTexture, NULL, pYUVFrame->data[0], pYUVFrame->linesize[0]);

					// 修正窗口大小变化
					sdlRect.x = 0;
					sdlRect.y = 0;
					sdlRect.w = screen_w;
					sdlRect.h = screen_h;

					// 渲染并显示
					SDL_RenderClear(sdlRenderer);
					SDL_RenderCopy(sdlRenderer, sdlTexture, NULL, &sdlRect);
					SDL_RenderPresent(sdlRenderer);
					videoFrameCnt++;
				}
				else if (event.type == SDL_WINDOWEVENT) { // 如果事件类型为窗口事件
					// 处理窗口大小变化
					SDL_GetWindowSize(screen, &screen_w, &screen_h);
				}
				else if (event.type == SDL_KEYDOWN && event.key.keysym.sym == SDLK_SPACE) {
					paused = ~paused;
				}
				else if (event.type == SDL_QUIT) { // 如果事件类型为退出事件
					thread_exit = 1; // 设置线程退出标志
				}
				else if (event.type == BREAK_EVENT) { // 如果事件类型为中断事件
					video_exit = 1;
					break; // 退出循环
				}
			}
		}
		if (packet->stream_index == audioIndex) {
			ret = avcodec_send_packet(pAudioCodecCtx, packet);
			if (ret < 0) {
				printf("Audio decode error.\n");
				return -1;
			}
			while (avcodec_receive_frame(pAudioCodecCtx, pAudioFrame) == 0) {
				printf("Decoded audio frame index: %d\n", audioFrameCnt);
				audioFrameCnt++;
				uint8_t* data;
				size_t dataSize;
				size_t samples;
				if (forceFormat != pAudioCodecCtx->sample_fmt || spec.freq != pAudioFrame->sample_rate || spec.channels != pAudioFrame->ch_layout.nb_channels)
					//重采样
				{
					//计算输入采样数
					int out_count = (int64_t)pAudioFrame->nb_samples * spec.freq / pAudioFrame->sample_rate + 256;
					//计算输出数据大小
					int out_size = av_samples_get_buffer_size(NULL, spec.channels, out_count, forceFormat, 0);
					//输入数据指针
					const uint8_t** in = (const uint8_t**)pAudioFrame->extended_data;
					//输出缓冲区指针
					uint8_t** out = &outBuffer;
					int len2 = 0;
					if (out_size < 0) {
						av_log(NULL, AV_LOG_ERROR, "av_samples_get_buffer_size() failed\n");
						return -1;
					}
					if (!swr_ctx)
						//初始化重采样对象
					{
						AVChannelLayout out_ch_layout, in_ch_layout = pAudioCodecCtx->ch_layout;
						av_channel_layout_default(&out_ch_layout, spec.channels);
						swr_alloc_set_opts2(&swr_ctx, &out_ch_layout, forceFormat, spec.freq, &in_ch_layout, pAudioCodecCtx->sample_fmt, pAudioCodecCtx->sample_rate, 0, NULL);
						if (!swr_ctx || swr_init(swr_ctx) < 0) {
							av_log(NULL, AV_LOG_ERROR, "swr_alloc_set_opts() failed\n");
							return -1;
						}
					}
					if (!outBuffer)
						//申请输出缓冲区
					{
						outBuffer = (uint8_t*)av_mallocz(out_size);
					}
					//执行重采样
					len2 = swr_convert(swr_ctx, out, out_count, in, pAudioFrame->nb_samples);
					if (len2 < 0) {
						av_log(NULL, AV_LOG_ERROR, "swr_convert() failed\n");
						return -1;
					}
					//取得输出数据
					data = outBuffer;
					//输出数据长度
					dataSize = av_samples_get_buffer_size(0, spec.channels, len2, forceFormat, 1);
					samples = len2;
				}
				else
				{
					data = pAudioFrame->data[0];
					dataSize = av_samples_get_buffer_size(pAudioFrame->linesize, pAudioFrame->ch_layout.nb_channels, pAudioFrame->nb_samples, forceFormat, 0);
					samples = pAudioFrame->nb_samples;
				}
				//写入队列
				while (1) {
					SDL_LockMutex(mtx);
					if (av_audio_fifo_space(fifo) >= samples)
					{
						av_audio_fifo_write(fifo, (void**)&data, samples);
						SDL_UnlockMutex(mtx);
						break;
					}
					SDL_UnlockMutex(mtx);
					//队列可用空间不足则延时等待
					//SDL_Delay((dataSize) * 1000.0 / (spec.freq * av_get_bytes_per_sample(forceFormat) * spec.channels) - 1);
				}
			}
		}
		av_packet_unref(packet);
	}
end:
	//销毁资源
	if (fifo)
		av_audio_fifo_free(fifo);
	if (audioId >= 2)
	{
		SDL_PauseAudioDevice(audioId, 1);
		SDL_CloseAudioDevice(audioId);
	}
	if (mtx)
		SDL_DestroyMutex(mtx);
	if (imgConvertCtx)
		sws_freeContext(imgConvertCtx);
	if (packet)
		av_packet_free(&packet);
	if (pYUVFrame)
		av_frame_free(&pYUVFrame);
	if (pVideoFrame)
		av_frame_free(&pVideoFrame);
	if (pAudioFrame)
		av_frame_free(&pAudioFrame);
	if (pVideoCodecCtx)
		avcodec_close(pVideoCodecCtx);
	if (pAudioCodecCtx)
		avcodec_close(pAudioCodecCtx);
	if (pFormatCtx)
		avformat_close_input(&pFormatCtx);
	av_dict_free(&opts);
	SDL_Quit();

	return 0;
}
```

