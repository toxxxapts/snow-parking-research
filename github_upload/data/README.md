# Dataset

The experiment uses **SPKLv2** from the authors of *Revising deep learning methods in parking lot occupancy detection*.

- Original repository: https://github.com/Eighonet/parking-research
- Paper: https://arxiv.org/abs/2306.04288
- Public archive ID currently configured in the supplied notebook: `1281KUAFuChRZAODO-ZTWSE-W2ilzmdxm`
- Corresponding download URL: https://drive.google.com/uc?export=download&id=1281KUAFuChRZAODO-ZTWSE-W2ilzmdxm

The original repository is the authoritative source if the archive link changes. The notebook tries to fetch only the required archive members using HTTP Range and checks member CRC values. It stores runtime data under `snowpark_v2/data`.

Raw frames, annotations and the full ZIP are not included in this repository. Keep the dataset local or in Colab rather than uploading the full archive to GitHub.

If online download fails, obtain `SPKLv2.zip` from the original source, upload it to Colab and set `LOCAL_ZIP = '/content/SPKLv2.zip'` in section 4. Use the real path if the filename or location differs.

The `Snow` tag alone does not prove heavy falling snow or hidden painted markings. Those conditions require independent review of the images and matched references. PKLot and CNRPark-EXT are background references, not data used by this notebook's experiments.
