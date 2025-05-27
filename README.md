# 🍓 Strawberry Analysis Project 🍓

 In HS495 class, we were tasked with training a deep learning model to detect ripe strawberries. Therefore, this project will evaluate and compare the performance of recent YOLO models (YOLOv11 and YOLOe) alongside a Qwen 2.5 VL model on a very small dataset. 

 ##  Dataset
 - [view the Dataset Here](https://huggingface.co/datasets/another-phytophile/StrawberryTrainingVariations)
- The original data set (V1) contained 63 images. 
- Later, I added 8 additional images. These were mostly null images, or images without any ripe strawberries to try to obtain a better precision. That is, I tried to add images with no ripe strawberries to make the model less likely to identify something that was not a raw strawberry as a raw strawberry. This version is called V4.
- For labeling, me, Shailesh Raj Acharya, and Steve Ameridge collaborated on labeling images. 

## Conclusion

Our results strongly support the conclusion that fine tuned modeled outperformed zero-shot models in most cases. While zero-shot performance with `YOLOE` achieved decent results, particularly with mAP at the 50-95 threshold, it consistently fell below even models fined-tuned with default parameters. With small model architectures like `YOLO` the cost of fine tuning is also small, with the most significant bottleneck being labeling and not compute. 

### Model Choice

| Model             | Precision | Recall | mAP50 | mAP50-95 |
|-------------------|-----------|--------|-------|----------|
| Yolo11 Default    | 0.715     | **0.735**  | 0.718 | 0.335    |
| Yolo11 More Epochs | 0.754     | 0.673  | 0.705 | 0.345    |
| Yolo11 Best of 10 | **0.809**     | 0.712  | **0.733** | 0.384    |
| Yolo11 Best of 274| 0.755     | 0.681  | 0.717 | 0.367    |
| YoloE             | 0.635     | 0.699  | 0.691 | **0.45**     |
| Qwen 2.5 VL       | 0.663     | 0.54   | 0.452 | 0.284    |

Overall Metric comparisons for the six models produced. Bolded represent the best metric in each category. note that the first two YOLO11 models were trained on a slightly different dataset than the other 4. 

## How to Run

- Notebooks/`Strawberry Detection.ipynb` contains the code to run the models (will require comyfui and roboflow accounts).

## Models

- [View the Finalized Finetuned Models Here](https://huggingface.co/another-phytophile/StrawberryModelVariation)