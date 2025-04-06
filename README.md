### Hackathon Report

> This is the public repository for __Group 6__ Hackathon __CX4803__

>[!Note]
> All steps to run this report are also included within the body of the report itself.

>[!Warning]
> This model was training and evaluated on an `A100` GPU provided by Google Colab, we can't guarantee the same performance or experience with other runtimes.

1. Start by cloning this repository with `git clone https://github.com/yifan-grace-tang/hackathon-report`
2. `cd hackathon-report` and make sure all the requisite files are in the current working directory: `sequence.fasta`, `train.csv`, `test.csv`. If you have any _query_ files that need to be appended to your training data make sure they are in the working directory as `query*.csv`
3. Run through the cells of the report, note that the `ProteinDataset` construction sets are quite computationally intensive on a first run-through as `ESM` embeddings are calculate. Subsequent reruns will not take as long since they will be cached in the local `esm-embeddings` directory:

```python
train_dataset_max = ProteinDataset(df_train, mode="max")
train_dataset_gauss = ProteinDataset(df_train, mode="gauss")
```
4. Finish running through the cells in succession, on the final step the test dataset construction will take an enormous amount of time so be wary of that.

```python
test_dataset_max = ProteinDataset(df_test, istrain=False, mode="max")
test_dataset_gauss = ProteinDataset(df_test, istrain=False, mode="gauss")
```
5. After running through the cells predictions and the top 10 information will be saved locally as `predictions.csv` and `top10.txt` respectivelly.
