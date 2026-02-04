# Alliance-Optimization-Model
This project generates data-driven alliance partner recommendations for FTC competitions using a Gradient Boosting approach (CatBoost) combined with a custom FitScore optimization framework. Scouting data from past and current is transformed into Auto and TeleOp points using DECODE season scoring constants, then rearranged into team performance profiles. CatBoost-style gradient boosting logic is used to weigh a teams performance, while explicit risk, redundancy, and coverage ensure rankings remain interpretable and accurate without bias. The final output is a downloadable PDF dashboard pack designed for fast alliance decisions at events.

Inputs:

Match scouting counts (Auto & Tele actions), Team number and match ID, Configured team of interest (TEAM_US)

Scoring:

Auto and TeleOp points are computed using locked DECODE scoring values, Total points = Auto + TeleOp, Dead matches are flagged when a team scores zero points

Model Logic:

Gradient Boosting (CatBoost) is used to weight performance signals

Teams are evaluated on-

Average scoring (ceiling), Consistency and reliability (variance, dead matches), Strategic fit (Auto vs Tele balance), Redundancy (overlapping scoring roles), A single FitScore (0–100) ranks teams for alliance selection

Key Features:

End-to-end Google Colab pipeline, Automatic data cleaning and validation, Risk-aware alliance ranking, Redundancy and role-coverage analysis, tournament-ready PDF dashboards

Outputs:

Ranked list of alliance partners, Visual comparisons across teams, Downloadable PDF scouting dashboards

Technologies:

Python, Pandas, NumPy

CatBoost (Gradient Boosting)

Matplotlib & Seaborn

Google Colab

Impact:

Provides a transparent, data-driven decision tool for alliance selection, helping FTC teams balance scoring potential, reliability, and strategic compatibility under competition constraints.

Developers: John Uy & Vishvak Gurram
