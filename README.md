# SenseVoiceDemo

This is a demo of [SenseVoice](https://github.com/FunAudioLLM/SenseVoice).

The `model.py` is copied from  [SenseVoice](https://github.com/FunAudioLLM/SenseVoice).

## How to run

1. Make sure you have installed `conda`.
2. Run `conda env create -f environment.yml` to create the environment.
3. Run `conda activate SenseVoiceTest` to activate the environment.
4. Download the pre-trained model from [modelscope](https://www.modelscope.cn/models/iic/sensevoicesmall) or [huggingface](https://huggingface.co/FunAudioLLM/SenseVoiceSmall).
   
   For example, download the model from modelscope and put it in the `model` folder:
   - Run `git lfs install` to install git-lfs;
   - Run `cd iic` to enter the `iic` folder;
   - Run `git clone https://www.modelscope.cn/iic/sensevoicesmall.git` to clone the model.
   - At the end, folder structure should be like this:
    ```
    SenseVoiceDemo
    |   .gitignore
    |   environment.yml
    |   LICENSE
    |   main.py
    |   model.py
    |   README.md
    |   requirements.txt
    |
    +---iic
    |   \---SenseVoiceSmall
    |       |   .gitattributes
    |       |   am.mvn
    |       |   chn_jpn_yue_eng_ko_spectok.bpe.model
    |       |   config.yaml
    |       |   configuration.json
    |       |   model.pt
    |       |   README.md
    |       |
    |       +---example
    |       |       .DS_Store
    |       |       en.mp3
    |       |       ja.mp3
    |       |       ko.mp3
    |       |       yue.mp3
    |       |       zh.mp3
    |       |
    |       \---fig
    |               aed_figure.png
    |               asr_results.png
    |               inference.png
    |               sensevoice.png
    |               ser_figure.png
    |               ser_table.png
     ```
5. Run `pip install -r requirements.txt` to install the required packages.
6. Run `python main.py` to run the demo.
7. By the way, If you have an NVIDIA GPU, you can modify the `device` in `main.py` to `cuda:0` to use GPU:
   ```python
    model = AutoModel(
        model=model_dir,
        trust_remote_code=True,
        remote_code="./model.py",  
        vad_model="fsmn-vad",
        vad_kwargs={"max_single_segment_time": 30000},
        device="cuda:0",
        # device="cpu",
    )
   ```