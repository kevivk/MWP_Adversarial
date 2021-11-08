### **Adversarial Examples for Evaluating Math Word Problem Solvers**
#### <span style="color:green"> *Accepted at EMNLP Findings 2021*


In this work we aim to evaluate the robustness of existing state-of-the-art MWP solvers by devising adversarial attacks.

We conduct our tests on three major solvers Graph2Tree, GTS and Seq2Seq models over two benchmark datasets present in English language namely AS-Div and MaWPS.

We observe on average a decline of over 40 pp in accuracy of these solvers. These evaluations were performed in two different settings using BERT and training from scratch.

**TRAINING COMMANDS:**

For graph2tree:

cd code/Graph2Tree

a) Train from Scratch
python -m src.main -mode train -gpu 0 -embedding_size 300 -hidden_size 256 -depth 2 -lr 0.0002 -emb_lr 8e-6 -batch_size 4 -epochs 50 -full_cv -run_name run_mawps_fold1 -save_model

b) Using BERT Embeddings: 

python -m src.main -mode train -gpu 0 -embedding -bert -bert_embedding_directory -embedding_size 300 -hidden_size 256 -depth 2 -lr 0.0002 -emb_lr 8e-6 -batch_size 4 -epochs 50 -full_cv -run_name run_mawps_fold1 -save_model


For GTS:

cd code/GTS

python -m src.main -mode train -gpu 0 -embedding -embedding_size 300 -hidden_size 256 -depth 2 -lr 0.0002 -emb_lr 8e-6 -batch_size 4 -epochs 50 -full_cv -run_name run_mawps_g2tee_fold1 -save_model

python -m src.main -mode train -gpu 0 -embedding -bert -bert_embedding_directory -embedding_size 300 -hidden_size 256 -depth 2 -lr 0.0002 -emb_lr 8e-6 -batch_size 4 -epochs 50 -full_cv -run_name run_mawps_g2tee_fold0 -save_model


**TEST COMMANDS:**

Graph2Tree:

cd code/Graph2Tree

python -m src.main -mode test -gpu 0 -embedding -embedding_size 300 -hidden_size 256 -depth 2 -lr 0.0002 -emb_lr 8e-6 -batch_size 4 -epochs 50 -no-full_cv -run_name run_mawps_g2tee_fold1_fold1

python -m src.main -mode test -gpu 0 -bert -bert_embedding_directory -embedding_size 300 -hidden_size 256 -depth 2 -lr 0.0002 -emb_lr 8e-6 -batch_size 4 -epochs 50 -no-full_cv -run_name run_mawps_g2tee_fold1_fold1

GTS : 

python -m src.main -mode test -gpu 0 -embedding -embedding_size 300 -hidden_size 256 -depth 2 -lr 0.0002 -emb_lr 8e-6 -batch_size 4 -epochs 50 -no-full_cv -run_name run_mawps_fold1_fold1

python -m src.main -mode test -gpu 0 -embedding -bert -bert_embedding_directory -embedding_size 300 -hidden_size 256 -depth 2 -lr 0.0002 -emb_lr 8e-6 -batch_size 4 -epochs 50 -no-full_cv -run_name run_mawps_fold1_fold1


Comment test_batch = final_adv_pair[0] line for simple evaluation.

Adversarial Examples of both Question reordering and Sentence Paraphrasing would be formed as a new output folder in Model directory.


We have utilized model implementations of MWP solvers from their respective repositories:

GTS: https://github.com/ShichaoSun/math_seq2tree

Graph2Tree: https://github.com/2003pro/Graph2Tree

Seq2Seq: https://github.com/arkilpatel/SVAMP

We have also referred to the repository https://github.com/arkilpatel/SVAMP and found it immensely useful.


Feel free to open a issue or mail us at vivek269611@gmail.com for any queries.

If you find our work useful please consider citing it using: 
```
@misc{kumar2021adversarial,
      title={Adversarial Examples for Evaluating Math Word Problem Solvers}, 
      author={Vivek Kumar and Rishabh Maheshwary and Vikram Pudi},
      year={2021},
      eprint={2109.05925},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
```


