```python
"""
该程序仅用于cosz毕业设计
本模块为主调用模块
最后修改日期：2022/4/11
最后修改内容：适配convnext网络
"""
import os
import shutil
import webbrowser
import tkinter as tk
from tkinter import filedialog
import crop_face
import predict


def input_mode():
    no1text = """
    ---------------------------------------------
    FakeMediaDetection v0.9               c o s z
    ---------------------------------------------
    请选择需要进入的模式数字，并按回车确定            ↓
    训练模式                                     1
    检测模式                                     2
    查看说明                                     3
    ---------------------------------------------
    
    """
    mode = input(no1text)
    return mode


def move_pretest_video():
    root = tk.Tk()
    root.withdraw()
    pretest_video_path = filedialog.askdirectory()
    # pretest_video_path = input("请输入待检测的视频所在根目录：\n")
    video_under_path = os.listdir(pretest_video_path)
    no2text = f"""
    ---------------------------------------------
    您输入的路径下查找到以下文件，请确认你需要的视频名称：
    {video_under_path}
    如果你想将目录下全部图片进行检测，请输入0
    ---------------------------------------------
    """
    video_choice = input(no2text)
    print(video_choice)
    if video_choice != "0":
        video_path = os.path.join(pretest_video_path, video_choice)
        now_path = "./detection/pre/" + video_choice
        shutil.copy(video_path, now_path)
        print("已成功选定视频移动到程序目录下\n")
    else:
        for i in range(len(video_under_path)):
            video_path = os.path.join(pretest_video_path, video_under_path[i])
            print(video_under_path[i])
            now_path = "./detection/pre/" + video_under_path[i]
            shutil.copy(video_path, now_path)


def check_dataset():
    no3text = """
    ---------------------------------------------
    FakeMediaDetection                    训练模式
    ---------------------------------------------
    请确保数据集满足以下条件：
    A. 视频格式，且视频中始终存在人脸
    B. 数据集已经区分好"fake"和"true"两类
    C. 请将数据集的"fake"和"true"放到./data/facefake
    
    确认后输入0以继续
    如果你使用Celeb-DF (v2)数据集，请输入1以继续
    ---------------------------------------------
    """
    no4text = """
    ---------------------------------------------
    提供以下工具以简化数据集处理：
    1. crop_face————————将数据集视频进行截帧和处理人脸
    2. make_csv—————————生成对执行crop后的图像进行划分
                        train和val的csv文件
    3. csv2file—————————根据生成的csv文件划分file路径
    4. move2onefile—————将分散的文件夹下文件重命名并移
                        动到一整个文件夹下
    
    如需使用请访问：
    https://github.com/INFWOLAD/SomeTools
    ---------------------------------------------
    
    """
    mode = input(no3text)
    if mode == "0":
        print("训练需要较长时间\n")
        os.system("./train.py")
        print("训练完成\n")
    elif mode == "1":
        print(no4text)
    else:
        print("输入错误,将退出\n")


def process_video():
    video_under_path = os.listdir("./detection/pre")
    with open("./detection/crop.txt", "w", encoding="utf-8") as process_txt:
        for i in range(len(video_under_path)):
            process_txt.write(f"0 {video_under_path[i]}\n")
    crop_face.main()
    print("已完成视频处理，处理图片保存在./detection/process")
    return video_under_path


def main():
    mode = input_mode()
    if mode == "1":
        check_dataset()
    elif mode == "2":
        move_pretest_video()
        video_under_path = process_video()
        for i in range(len(video_under_path)):
            print(video_under_path[i])
            predict.main("./detection/process/" + video_under_path[i].split('.')[0] + "_0.png")
        print("已完成检测")
    elif mode == "3":
        webbrowser.open("https://cosz.netlify.app/FakeMediaDetection.html")
    else:
        print("输入错误，请重新输入\n")


if __name__ == '__main__':
    main()
```