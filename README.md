# Content analysis in astroturfing detection

Code for *A jagged reading: Telling amplification from astroturfing in a pre-election anti-migrant surge on UK Reddit*

The study collects migration-related comments from UK political subreddits around the 7 May 2026 local elections (8 March – 8 June 2026), classifies their stance with StanceBERTa and a local LLM (Ministral-14B), and tests the anti-migrant comments, and the accounts that posted them, for features of astroturfing. Everything is in one notebook, `Reform_Reddit_Election_CLEAN.ipynb`, organised by research question; its saved outputs show every result and figure in the paper.

## Figures

| File | In the paper |
|---|---|
| `figures/figure3_S9_comparison.png` | Figure 3: religious vocabulary (USAS S9) |
| `figures/figure4_ai_ese_markers.png` | Figure 4: AI-ese markers |
| `figures/figure5_anti_migrant_share.png` | Figure 5: daily anti-migrant share |
| `figures/table2_topic_vs_hostility.png` | Table 2, as a chart |
| `figures/figure6_account_creation.png` | Figure 6: account creation dates |
| `figures/network_communities.png` | Figure 8: Network of strongly tied accounts |
| `figures/figureA1_S9_anti_migrant.png`, `figureA2_S9_control.png` | Figures A1 and A2 |

## Running it

```bash
pip install -r requirements.txt
python -m spacy download en_core_web_sm
```

The PyMUSAS English tagger (`en_dual_none_contextual`, version 0.3.3) is installed from the [PyMUSAS models releases](https://github.com/UCREL/pymusas-models/releases).

Paths and switches are in the notebook's Settings cell. With every switch off (the default) the notebook reproduces the paper from saved data in about five minutes; each switch re-runs one step (Reddit collection, StanceBERTa, Ministral, gold-standard tests, account audit, Arctic Shift download, deletion check). Reddit API credentials go in a `.env` file copied from `.env.example`.

## Data and ethics

The Reddit comments, usernames and derived data files are not included in this repository. All comments analysed were public, but the paper reports results in aggregate only and does not identify individual accounts; the notebook prints no usernames or comment text. Re-collecting through the Reddit API (`RECOLLECT_DATA = True`) produces a new, similar but not identical, sample, because comments and accounts change over time; comment histories are available from the [Arctic Shift](https://arctic-shift.photon-reddit.com) archive.
