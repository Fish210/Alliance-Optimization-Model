# Alliance-Optimization-Model
This project generates data-driven alliance partner recommendations for FTC competitions using a Gradient Boosting approach (CatBoost) combined with a custom FitScore optimization framework. Scouting data from past and current is transformed into Auto and TeleOp points using DECODE season scoring constants, then rearranged into team performance profiles. CatBoost-style gradient boosting logic is used to weigh a teams performance, while explicit risk, redundancy, and coverage ensure rankings remain interpretable and accurate without bias. The final output is a downloadable PDF dashboard pack designed for fast alliance decisions at events.

Model Inputs (from CSV)

Match-level scouting counts

auto_leave

auto_artifact_cl_count, auto_artifact_overflow_count, auto_motif_match_count

tele_artifact_cl_count, tele_artifact_overflow_count, tele_motif_match_count, tele_depot_count

team, match_id

Configuration

TEAM_US (our team number, e.g., 3470)

Scoring Engine (DECODE locked constants)

Counts are converted to points using official season weights:

Auto Points = 3·leave + 3·CL + 1·overflow + 2·motif

Tele Points = 3·CL + 1·overflow + 2·motif + 1·depot

Total Points = auto + tele

Dead Match Flag = 1 if total == 0

Gradient Boosting + FitScore Optimization

The model combines CatBoost-style gradient boosting principles with explicit, explainable metrics:

Boosted performance signals

Mean total points (ceiling)

Auto vs Tele specialization

Match-to-match stability

Risk & strategy constraints

Risk penalty: point variance + dead-match rate

Redundancy penalty: cosine similarity between scoring fingerprints

Coverage bonus: boosts teams that outperform us in our weaker phase

Core logic:

expected_alliance_points = our_mean + team_mean

fit_raw = expected_alliance_points − risk_penalty − redundancy + coverage_bonus

fit_score normalized to 0–100 for ranking

This hybrid approach preserves the predictive strength of gradient boosting while maintaining human-readable decision logic for judges and drive teams.

Key Features

Gradient Boosting (CatBoost-inspired) alliance evaluation

End-to-end Colab pipeline (single run)

Automatic data cleaning and validation

Robust handling of dead matches and high-variance teams

Strategic redundancy detection and role-coverage modeling

Dark-mode, tournament-ready PDF dashboards

Stable next-match point prediction (recent-weighted)

Outputs

Ranked alliance partners by FitScore

FTC_Dashboards_Dark.pdf with:

global heatmaps and rankings

ceiling vs risk scatter plots

per-team strategic breakdown pages

Downloadable, Google Sheets–ready data

Technologies

Python, Pandas, NumPy

CatBoost (Gradient Boosting methodology)

Matplotlib & Seaborn

Google Colab

Impact

Demonstrates the application of gradient boosting, data ethics, and explainable decision-support systems in a competitive FTC environment—helping teams select alliances that maximize scoring potential while minimizing risk and strategic overlap.

Developers

John Uy & Vishvak Gurram
