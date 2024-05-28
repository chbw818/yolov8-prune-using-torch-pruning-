prune yolov8 using torch-pruning
===
[prune_v8.py](https://github.com/chbw818/yolov8-prune-using-torch-pruning-/blob/main/prune_v8.py) modify the code in [yolov8_pruning.py](https://github.com/VainF/Torch-Pruning/blob/master/examples/yolov8/yolov8_pruning.py) to make it suitable for 
the newest version of [yolov8](https://github.com/ultralytics/ultralytics).<br>
To be specific,I mainly modified lines 15 to 21 and `lines 251`.<br>
Before run `prune_v8.py`,you need to replace the `loss.py` in `ultralytics-main\ultralytics\utils\loss.py` with the [loss.py](https://github.com/chbw818/yolov8-prune-using-torch-pruning-/blob/main/loss.py)<br>
Or you could simply add these lines before [line192 in loss.py](https://github.com/ultralytics/ultralytics/blob/main/ultralytics/utils/loss.py#L192)<br>
```python
mydevice=torch.device('cuda:0')<br>
self.proj=self.proj.to(mydevice)
```
you can simply run prune_v8.py by `python prune_v8.py` after modifying the correct model path and dataset path in `line 387` and `line 285`<br>
You could use `python detect_prune.py` to test the performance of the pruned model
