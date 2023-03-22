
本次作業使用JDE作為tracking model,使用其github提供之pre-trained weights

Requirements
Python 3.6
Pytorch >= 1.2.0
python-opencv
py-motmetrics (pip install motmetrics)
cython-bbox (pip install cython_bbox)
lap==0.4.0

(Optional) ffmpeg (used in the video demo)
(Optional) syncbn (compile and place it under utils/syncbn, or simply replace with nn.BatchNorm here)

""""""""""""""""""""""""""""
有修改之code
在解壓縮後一進去看到的檔案裡(先稱為root)
demo.py
demo_select.py
demowebcam.py
demowebcam_select.py

track.py
track_select.py
進入utils資料夾裡(root/utils)
datasets.py
datasetswebcam.py
visualization.py
""""""""""""""""""""""""""""

進入資料夾
for general usage ->video放在assets資料夾 結束會在assets/your_output_folder 生成frame資料夾(逐偵結果) result.mp4 result.txt(全部結果做成影片和txt檔) 

python demo.py --input-video assets/your_input_video.py --weights jde.1088x608.uncertainty.pt --output-root assets/your_output_folder 

本次使用指令
video input 指令

#長按住track_id%10對應數字鍵取消特定人物 放開顯示所有人物
python demo.py --input-video assets/test.mp4 --weights jde.1088x608.uncertainty.pt --output-root assets/demo1

#須長按住s顯示所有人物 長按住track_id%10對應數字鍵選擇特定人物 全不按只會有數字不會有框
python demo_select.py --input-video assets/test.mp4 --weights jde.1088x608.uncertainty.pt --output-root assets/demo2


camera input 指令


#長按住track_id%10對應數字鍵取消特定人物 放開顯示所有人物
python demowebcam.py --weights jde.1088x608.uncertainty.pt --output-root assets/demo3



#須長按住s顯示所有人物 長按住track_id%10對應數字鍵選擇特定人物 全不按只會有數字不會有框
python demowebcam_select.py --weights jde.1088x608.uncertainty.pt --output-root assets/demo4



分兩份code 分別做video input 和camera input


分兩份code 分別做cancel select
demo.py demowebcam.py用來CANCEL

demo_select demowebcam_select用來SELECT

reference: https://github.com/Zhongdao/Towards-Realtime-MOT

附上pt來源
在上述JDE reference github 中提供Pretrained model and baseline models部分中的weight "JDE-1088x608"
連結：https://drive.google.com/file/d/1nlnuYfGNuHWZztQHXwVZSL_FvfE551pA/view
載下來會是jde.1088x608.uncertainty.pt 放在一解壓縮完打開的地方(和demo.py同層)