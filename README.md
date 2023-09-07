# deChaisemartin-2020

## 概要
de Chaisemartin and D'Haultf\[oe\]uille (2020)に関するシミュレーションを行う。Baker (2022)をベースにデータを生成し、de Chaisemartin and D'Haultf\[oe\]uilleの手法（以下、dCDH）による推定値をTwo-way fixed effectモデル（以下、TWFE）と比較する。\\
Baker (2022)は1989年から2007年までの36年間における米国1000社のROA (Return on Asset)を用いるという設定でデータのシミュレーションを行った。元論文ではStaggered DiDを仮定し、1989年、1998年、2007年に1/3ずつのサンプルに処置を施すという状況を想定していた。今回はサンプルを4分割して、「1989年に処置を受けるが、1998年以降処置を打ち止める」というグループを追加する。\\
ROAの生成過程については、Baker (2022)のsimulation3~6を参照する。すべてのシミュレーションで共通するのが企業固定効果と時間固定効果、誤差項で、それぞれ$N(0,0.5^2)$に従う。ここに処置を受けている期間のみ、処置効果を加える。処置効果の取り方は各シミュレーションによって異なる。Simulatin3では、処置効果が常に$N(0,0.2^{2})$に従う。Simulation4では処置効果がグループによって異なり、1989年に処置を受ける企業の処置効果は$N(5,0.2^2)$に従う。

de Chaisemartin, C., and D'Haultf\[oe\]uille, X. 2020. Difference-in-differences with multiple time periods, Jornal of Econometrics,  225(2), 200-230
