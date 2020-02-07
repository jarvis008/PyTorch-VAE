<h1 align="center">
  <b>PyTorch VAE</b><br>
</h1>

<p align="center">
      <a href="https://www.python.org/">
        <img src="https://img.shields.io/badge/Python-3.5-ff69b4.svg" /></a>
       <a href= "https://pytorch.org/">
        <img src="https://img.shields.io/badge/PyTorch-1.3-2BAF2B.svg" /></a>
       <a href= "https://github.com/AntixK/PyTorch-VAE/blob/master/LICENSE.md">
        <img src="https://img.shields.io/badge/license-Apache2.0-blue.svg" /></a>
         <a href= "https://twitter.com/intent/tweet?text=PyTorch-VAE:%20Collection%20of%20VAE%20models%20in%20PyTorch.&url=https://github.com/AntixK/PyTorch-VAE">
        <img src="https://img.shields.io/twitter/url/https/shields.io.svg?style=social" /></a>

</p>

A collection of Variational AutoEncoders (VAEs) implemented in PyTorch with focus on reproducibility. The aim of this project is to provide
a quick and simple working example for many of the cool VAE models out there. All the models are trained on the [CelebA dataset](http://mmlab.ie.cuhk.edu.hk/projects/CelebA.html)
for consistency and comparison. The architecture of all the models are kept as similar as possible with the same layers, except for cases where the original paper necessitates a radically different architecture.
Here are the [results](https://github.com/AntixK/PyTorch-VAE/blob/master/README.md#--results) of each model.

### Requirements
- Python >= 3.5
- PyTorch >= 1.3
- Pytorch Lightning >= 0.6.0 ([GitHub Repo](https://github.com/PyTorchLightning/pytorch-lightning/tree/deb1581e26b7547baf876b7a94361e60bb200d32))
- CUDA enabled computing device

### Installation
```
$ git clone https://github.com/AntixK/PyTorch-VAE
$ cd PyTorch-VAE
$ pip install -r requirements.txt
```

### Usage
```
$ cd PyTorch-VAE
$ python run.py -c configs/<config-file-name.yaml>
```
**Config file template**
```yaml
model_params:
  name: "<name of VAE model>"
  in_channels: 3
  latent_dim: 
    .         # Other parameters required by the model
    .
    .

exp_params:
  data_path: "<path to the celebA dataset>"
  img_size: 64    # Models are designed to work for this size
  batch_size: 64  # Better to have a square number
  LR: 0.005
  weight_decay:
    .         # Other arguments required for training, like scheduler etc.
    .
    .

trainer_params:
  gpus: 1         
  max_nb_epochs: 50
  gradient_clip_val: 1.5
    .
    .
    .

logging_params:
  save_dir: "logs/"
  name: "<experiment name>"
  manual_seed: 
```


----
<h2 align="center">
  <b>Results</b><br>
</h2>


| Model                               | Paper                                            |Reconstruction | Samples |
|-------------------------------------|--------------------------------------------------|---------------|---------|
| VAE [Code][vae_code]                   |[Link](https://arxiv.org/abs/1312.6114)           |    ![][2]     | ![][1]  |
| Conditional VAE [Code][cvae_code]      |[Link](https://openreview.net/forum?id=rJWXGDWd-H)|    ![][16]    | ![][15] |
| WAE - MMD (RBF Kernel) [Code][wae_code]|[Link](https://arxiv.org/abs/1711.01558)          |    ![][4]     | ![][3]  |
| WAE - MMD (IMQ Kernel) [Code][wae_code]|[Link](https://arxiv.org/abs/1711.01558)          |    ![][6]     | ![][5]  |
| Beta-VAE [Code][bvae_code]             |[Link](https://openreview.net/forum?id=Sy2fzU9gl) |    ![][8]     | ![][7]  |
| Disentangled Beta-VAE [Code][bvae_code]|[Link](https://arxiv.org/abs/1804.03599)          |    ![][22]    | ![][21] |
| IWAE (5 Samples) [Code][iwae_code]     |[Link](https://arxiv.org/abs/1509.00519)          |    ![][10]    | ![][9]  |
| DFCVAE   [Code][dfcvae_code]           |[Link](https://arxiv.org/abs/1610.00291)          |    ![][12]    | ![][11] |
| MSSIM VAE    [Code][mssimvae_code]     |[Link](https://arxiv.org/abs/1511.06409)          |    ![][14]    | ![][13] |
| Categorical VAE   [Code][catvae_code]  |[Link](https://arxiv.org/abs/1611.01144)          |    ![][18]    | ![][17] |
| Joint VAE [Code][jointvae_code]        |[Link](https://arxiv.org/abs/1804.00104)          |    ![][20]    | ![][19] |
| Info VAE   [Code][infovae_code]        |[Link](https://arxiv.org/abs/1706.02262)          |    ![][24]    | ![][23] |
| LogCosh VAE   [Code][logcoshvae_code]  |[Link](https://openreview.net/forum?id=rkglvsC9Ym)|    ![][26]    | ![][25] |
| SWAE (50 Projections) [Code][swae_code]|[Link](https://arxiv.org/abs/1804.01947)          |    ![][28]    | ![][27] |



<!-- | Gamma VAE             |[Link](https://arxiv.org/abs/1610.05683)          |    ![][16]    | ![][15] |-->




### TODO
- [x] VanillaVAE
- [x] Beta VAE
- [x] DFC VAE
- [x] MSSIM VAE
- [x] IWAE
- [x] WAE-MMD
- [x] Conditional VAE
- [x] Categorical VAE (Gumbel-Softmax VAE)
- [x] Joint VAE
- [x] Disentangled beta-VAE
- [x] InfoVAE
- [x] LogCosh VAE
- [ ] SWAE (in progress)
- [ ] Ladder VAE (in progress)
- [ ] Gamma VAE (in progress) 
- [ ] Vamp VAE (in progress)
- [ ] HVAE (VAE with Vamp Prior) (in progress)
- [ ] Beta TC-VAE
- [ ] PixelVAE
- [ ] VQVAE


### Contributing
If you have trained a better model, using these implementations, by fine-tuning the hyper-params in the config file,
I would be happy to include your result (along with your config file) in this repo, citing your name 😊.

### License
**Apache License 2.0**

| Permissions      | Limitations       | Conditions                       |
|------------------|-------------------|----------------------------------|
| ✔️ Commercial use |  ❌  Trademark use |  ⓘ License and copyright notice | 
| ✔️ Modification   |  ❌  Liability     |  ⓘ State changes                |
| ✔️ Distribution   |  ❌  Warranty      |                                  |
| ✔️ Patent use     |                   |                                  |
| ✔️ Private use    |                   |                                  |


### Citation
```
@misc{Subramanian2020,
  author = {Subramanian, A.K},
  title = {PyTorch-VAE},
  year = {2020},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/AntixK/PyTorch-VAE}}
}
```
-----------

[vae_code]: https://github.com/AntixK/PyTorch-VAE/blob/master/models/vanilla_vae.py
[cvae_code]: https://github.com/AntixK/PyTorch-VAE/blob/master/models/cvae.py
[bvae_code]: https://github.com/AntixK/PyTorch-VAE/blob/master/models/beta_vae.py
[wae_code]: https://github.com/AntixK/PyTorch-VAE/blob/master/models/wae_mmd.py
[iwae_code]: https://github.com/AntixK/PyTorch-VAE/blob/master/models/iwae.py
[swae_code]: https://github.com/AntixK/PyTorch-VAE/blob/master/models/swae.py
[jointvae_code]: https://github.com/AntixK/PyTorch-VAE/blob/master/models/joint_vae.py
[dfcvae_code]: https://github.com/AntixK/PyTorch-VAE/blob/master/models/dfcvae.py
[mssimvae_code]: https://github.com/AntixK/PyTorch-VAE/blob/master/models/mssim_vae.py
[logcoshvae_code]: https://github.com/AntixK/PyTorch-VAE/blob/master/models/logcosh_vae.py
[catvae_code]: https://github.com/AntixK/PyTorch-VAE/blob/master/models/cat_vae.py



[1]: https://github.com/AntixK/PyTorch-VAE/blob/master/assets/Vanilla%20VAE_25.png
[2]: https://github.com/AntixK/PyTorch-VAE/blob/master/assets/recons_Vanilla%20VAE_25.png
[3]: https://github.com/AntixK/PyTorch-VAE/blob/master/assets/WAE_RBF_18.png
[4]: https://github.com/AntixK/PyTorch-VAE/blob/master/assets/recons_WAE_RBF_19.png
[5]: https://github.com/AntixK/PyTorch-VAE/blob/master/assets/WAE_IMQ_15.png
[6]: https://github.com/AntixK/PyTorch-VAE/blob/master/assets/recons_WAE_IMQ_15.png
[7]: https://github.com/AntixK/PyTorch-VAE/blob/master/assets/BetaVAE_H_20.png
[8]: https://github.com/AntixK/PyTorch-VAE/blob/master/assets/recons_BetaVAE_H_20.png
[9]: https://github.com/AntixK/PyTorch-VAE/blob/master/assets/IWAE_19.png
[10]: https://github.com/AntixK/PyTorch-VAE/blob/master/assets/recons_IWAE_19.png
[11]: https://github.com/AntixK/PyTorch-VAE/blob/master/assets/DFCVAE_49.png
[12]: https://github.com/AntixK/PyTorch-VAE/blob/master/assets/recons_DFCVAE_49.png
[13]: https://github.com/AntixK/PyTorch-VAE/blob/master/assets/MSSIMVAE_29.png
[14]: https://github.com/AntixK/PyTorch-VAE/blob/master/assets/recons_MSSIMVAE_29.png
[15]: https://github.com/AntixK/PyTorch-VAE/blob/master/assets/ConditionalVAE_20.png
[16]: https://github.com/AntixK/PyTorch-VAE/blob/master/assets/recons_ConditionalVAE_20.png
[17]: https://github.com/AntixK/PyTorch-VAE/blob/master/assets/CategoricalVAE_49.png
[18]: https://github.com/AntixK/PyTorch-VAE/blob/master/assets/recons_CategoricalVAE_49.png
[19]: https://github.com/AntixK/PyTorch-VAE/blob/master/assets/JointVAE_49.png
[20]: https://github.com/AntixK/PyTorch-VAE/blob/master/assets/recons_JointVAE_49.png
[21]: https://github.com/AntixK/PyTorch-VAE/blob/master/assets/BetaVAE_B_35.png
[22]: https://github.com/AntixK/PyTorch-VAE/blob/master/assets/recons_BetaVAE_B_35.png
[23]: https://github.com/AntixK/PyTorch-VAE/blob/master/assets/InfoVAE_31.png
[24]: https://github.com/AntixK/PyTorch-VAE/blob/master/assets/recons_InfoVAE_31.png
[25]: https://github.com/AntixK/PyTorch-VAE/blob/master/assets/LogCoshVAE_49.png
[26]: https://github.com/AntixK/PyTorch-VAE/blob/master/assets/recons_LogCoshVAE_49.png
[27]: https://github.com/AntixK/PyTorch-VAE/blob/master/assets/SWAE_49.png
[28]: https://github.com/AntixK/PyTorch-VAE/blob/master/assets/recons_SWAE_49.png

[python-image]: https://img.shields.io/badge/Python-3.5-ff69b4.svg
[python-url]: https://www.python.org/

[pytorch-image]: https://img.shields.io/badge/PyTorch-1.3-2BAF2B.svg
[pytorch-url]: https://pytorch.org/

[twitter-image]:https://img.shields.io/twitter/url/https/shields.io.svg?style=social
[twitter-url]:https://twitter.com/intent/tweet?text=Neural%20Blocks-Easy%20to%20use%20neural%20net%20blocks%20for%20fast%20prototyping.&url=https://github.com/AntixK/NeuralBlocks


[license-image]:https://img.shields.io/badge/license-Apache2.0-blue.svg
[license-url]:https://github.com/AntixK/PyTorch-VAE/blob/master/LICENSE.md
