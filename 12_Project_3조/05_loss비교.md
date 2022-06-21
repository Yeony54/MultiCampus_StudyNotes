돌릴 것

resnet, 1e-4
nadam

resnet, 1e-5
전체

efficientnet, 1e-3
rmsprop, nadam

efficientnet, 1e-4/1e-5 전체

regnet,1e-3
rmsprop, nadam

regnet, 1e-4 전체

regnet,1e-5
~~adam~~,, rmsprop, nadam


돌리고 있는것

혜주: 1e-5 모두(local, colab)
지연: aws(1e-4 모두), 
colab(efficientnet- 1e-3 rmsprop, nadam, 
regnet- 1e-3 rmsprop, nadam)



| resnet  | 1e-3                                 | 1e-4                                 | 1e-5                                 |
| ------- | ------------------------------------ | ------------------------------------ | ------------------------------------ |
| lamb    | **<span style="color:red">o</span>** | x 지연                               | **<span style="color:red">o</span>** |
| adam    | **<span style="color:red">o</span>** | **<span style="color:red">o</span>** | x 혜주                               |
| rmsprop | **<span style="color:red">o</span>** | - 지연                               | x 인후                               |
| nadam   | x 지연                               | x 지연                               | x 인후                               |

| efficientnet | 1e-3                                 | 1e-4 | 1e-5                                 |
| ------------ | ------------------------------------ | ---- | ------------------------------------ |
| lamb         | **<span style="color:red">o</span>** | x    | **<span style="color:red">o</span>** |
| adam         | **<span style="color:red">o</span>** | x    | x                                    |
| rmsprop      | x                                    | x    | x                                    |
| nadam        | x                                    | x    | x                                    |

| regnet  | 1e-3                                 | 1e-4 | 1e-5                                 |
| ------- | ------------------------------------ | ---- | ------------------------------------ |
| lamb    | **<span style="color:red">o</span>** | x    | **<span style="color:red">o</span>** |
| adam    | **<span style="color:red">o</span>** | x    | **<span style="color:red">o</span>** |
| rmsprop | x                                    | x    | - 혜주                               |
| nadam   | x                                    | x    | x                                    |



# AWS

### ResNet50_adam_0.01

model : ResNet50
optimizer : adam, learning rate : 0.01
Epoch [1] Train loss : [3.67931] Validation loss : [8.93642]

------------------ Model Saved ------------------
Epoch [2] Train loss : [2.51474] Validation loss : [2.19357]

------------------ Model Saved ------------------
Epoch [3] Train loss : [2.48762] Validation loss : [1.97305]

------------------ Model Saved ------------------
Epoch [4] Train loss : [2.34774] Validation loss : [1.96784]

------------------ Model Saved ------------------
Epoch [5] Train loss : [2.19224] Validation loss : [1.74296]

------------------ Model Saved ------------------
Epoch [6] Train loss : [2.04479] Validation loss : [2.17464]
Epoch [7] Train loss : [1.97287] Validation loss : [1.61343]

------------------ Model Saved ------------------
Epoch [8] Train loss : [1.93758] Validation loss : [1.63981]
Epoch [9] Train loss : [1.79096] Validation loss : [1.34088]

------------------ Model Saved ------------------
Epoch [10] Train loss : [1.67301] Validation loss : [1.59403]
Epoch [11] Train loss : [1.61258] Validation loss : [1.21352]

------------------ Model Saved ------------------
Epoch [12] Train loss : [1.57090] Validation loss : [1.52932]
Epoch [13] Train loss : [1.41193] Validation loss : [1.04900]

------------------ Model Saved ------------------
Epoch [14] Train loss : [1.33975] Validation loss : [1.38810]
Epoch [15] Train loss : [1.30636] Validation loss : [1.31113]
Epoch [16] Train loss : [1.22744] Validation loss : [1.05763]
Epoch [17] Train loss : [1.09751] Validation loss : [1.31033]
Epoch [18] Train loss : [1.08376] Validation loss : [1.00915]

------------------ Model Saved ------------------
Epoch [19] Train loss : [0.97861] Validation loss : [0.52311]

------------------ Model Saved ------------------
Epoch [20] Train loss : [0.89242] Validation loss : [2.26861]
Epoch [21] Train loss : [0.88378] Validation loss : [0.48841]

------------------ Model Saved ------------------
Epoch [22] Train loss : [0.79195] Validation loss : [0.53082]
Epoch [23] Train loss : [0.82133] Validation loss : [0.76326]
Epoch [24] Train loss : [0.68718] Validation loss : [0.33341]

------------------ Model Saved ------------------
Epoch [25] Train loss : [0.68859] Validation loss : [0.31862]

------------------ Model Saved ------------------
Epoch [26] Train loss : [0.66302] Validation loss : [0.49465]
Epoch [27] Train loss : [0.62579] Validation loss : [0.94647]
Epoch [28] Train loss : [0.62701] Validation loss : [0.52526]
Epoch [29] Train loss : [0.57400] Validation loss : [0.20725]

------------------ Model Saved ------------------
Epoch [30] Train loss : [0.57508] Validation loss : [1.35349]
Epoch [31] Train loss : [0.49631] Validation loss : [0.24051]
Epoch [32] Train loss : [0.47777] Validation loss : [0.31096]
Epoch [33] Train loss : [0.45840] Validation loss : [0.52607]
Epoch [34] Train loss : [0.39008] Validation loss : [0.13567]

------------------ Model Saved ------------------
Epoch [35] Train loss : [0.42898] Validation loss : [0.26696]
Epoch [36] Train loss : [0.42368] Validation loss : [0.34174]
Epoch [37] Train loss : [0.37962] Validation loss : [0.14376]
Epoch [38] Train loss : [0.36619] Validation loss : [0.53986]
Epoch [39] Train loss : [0.39059] Validation loss : [0.17555]
Epoch [40] Train loss : [0.34049] Validation loss : [0.11075]

------------------ Model Saved ------------------
Epoch [41] Train loss : [0.30962] Validation loss : [0.16641]
Epoch [42] Train loss : [0.37700] Validation loss : [0.77996]
Epoch [43] Train loss : [0.30800] Validation loss : [0.31777]
Epoch [44] Train loss : [0.30617] Validation loss : [0.54863]
Epoch [45] Train loss : [0.30645] Validation loss : [0.16574]
Epoch [46] Train loss : [0.25472] Validation loss : [0.03725]

------------------ Model Saved ------------------
Epoch [47] Train loss : [0.27715] Validation loss : [0.23082]
Epoch [48] Train loss : [0.27176] Validation loss : [0.07507]
Epoch [49] Train loss : [0.25518] Validation loss : [0.98590]
Epoch [50] Train loss : [0.30270] Validation loss : [0.29377]

### ResNet50_rmsprop_0.01

model : ResNet50
optimizer : rmsprop, learning rate : 0.01
Epoch [1] Train loss : [40.48962] Validation loss : [2.46437]

------------------ Model Saved ------------------
Epoch [2] Train loss : [2.59879] Validation loss : [2.61376]
Epoch [3] Train loss : [2.54917] Validation loss : [2.37936]

------------------ Model Saved ------------------
Epoch [4] Train loss : [2.49314] Validation loss : [2.26711]

------------------ Model Saved ------------------
Epoch [5] Train loss : [2.50805] Validation loss : [2.27068]
Epoch [6] Train loss : [2.48965] Validation loss : [2.32764]
Epoch [7] Train loss : [2.49127] Validation loss : [2.21811]

------------------ Model Saved ------------------
Epoch [8] Train loss : [2.47148] Validation loss : [2.07883]

------------------ Model Saved ------------------
Epoch [9] Train loss : [2.43875] Validation loss : [2.09950]
Epoch [10] Train loss : [2.37369] Validation loss : [1.98026]

------------------ Model Saved ------------------
Epoch [11] Train loss : [2.35162] Validation loss : [1.86423]

------------------ Model Saved ------------------
Epoch [12] Train loss : [2.36530] Validation loss : [2.25747]
Epoch [13] Train loss : [2.41429] Validation loss : [1.98293]
Epoch [14] Train loss : [2.36092] Validation loss : [2.03869]
Epoch [15] Train loss : [2.35530] Validation loss : [1.96586]
Epoch [16] Train loss : [2.29450] Validation loss : [2.02532]
Epoch [17] Train loss : [2.30405] Validation loss : [1.84429]

------------------ Model Saved ------------------
Epoch [18] Train loss : [2.28531] Validation loss : [6.43915]
Epoch [19] Train loss : [2.24542] Validation loss : [1.79258]

------------------ Model Saved ------------------
Epoch [20] Train loss : [2.14253] Validation loss : [2.09341]
Epoch [21] Train loss : [2.10515] Validation loss : [1.72588]

------------------ Model Saved ------------------
Epoch [22] Train loss : [1.90704] Validation loss : [1.97702]
Epoch [23] Train loss : [1.90595] Validation loss : [1.71357]

------------------ Model Saved ------------------
Epoch [24] Train loss : [1.76430] Validation loss : [1.29101]

------------------ Model Saved ------------------
Epoch [25] Train loss : [1.72585] Validation loss : [1.63108]
Epoch [26] Train loss : [1.66090] Validation loss : [1.29266]
Epoch [27] Train loss : [1.67997] Validation loss : [1.29887]
Epoch [28] Train loss : [1.57469] Validation loss : [1.05261]

------------------ Model Saved ------------------
Epoch [29] Train loss : [1.50301] Validation loss : [2.27406]
Epoch [30] Train loss : [1.31291] Validation loss : [0.97062]

------------------ Model Saved ------------------
Epoch [31] Train loss : [2.35941] Validation loss : [1.39999]
Epoch [32] Train loss : [1.65667] Validation loss : [1.45003]
Epoch [33] Train loss : [1.55496] Validation loss : [1.08435]
Epoch [34] Train loss : [1.53606] Validation loss : [1.67725]
Epoch [35] Train loss : [1.42151] Validation loss : [1.02523]
Epoch [36] Train loss : [1.32878] Validation loss : [0.88909]

------------------ Model Saved ------------------
Epoch [37] Train loss : [1.24369] Validation loss : [0.97435]
Epoch [38] Train loss : [1.22609] Validation loss : [1.22947]
Epoch [39] Train loss : [1.11146] Validation loss : [0.75413]

------------------ Model Saved ------------------
Epoch [40] Train loss : [0.98839] Validation loss : [1.38685]
Epoch [41] Train loss : [0.86709] Validation loss : [0.63083]

------------------ Model Saved ------------------
Epoch [42] Train loss : [0.94363] Validation loss : [0.47116]

------------------ Model Saved ------------------
Epoch [43] Train loss : [0.73196] Validation loss : [1.97236]
Epoch [44] Train loss : [0.70366] Validation loss : [0.42735]

------------------ Model Saved ------------------
Epoch [45] Train loss : [0.70799] Validation loss : [0.45902]
Epoch [46] Train loss : [0.91328] Validation loss : [0.35975]

------------------ Model Saved ------------------
Epoch [47] Train loss : [0.57152] Validation loss : [0.58416]
Epoch [48] Train loss : [0.68553] Validation loss : [0.36410]
Epoch [49] Train loss : [0.60674] Validation loss : [0.26958]

------------------ Model Saved ------------------
Epoch [50] Train loss : [0.57770] Validation loss : [0.22551]

### ResNet50_nadam_0.01

model : ResNet50
optimizer : nadam, learning rate : 0.01
Epoch [1] Train loss : [3.27952] Validation loss : [2.30640]

------------------ Model Saved ------------------
Epoch [2] Train loss : [2.49834] Validation loss : [2.30899]
Epoch [3] Train loss : [2.47987] Validation loss : [2.29367]

------------------ Model Saved ------------------
Epoch [4] Train loss : [2.42001] Validation loss : [1.96761]

------------------ Model Saved ------------------
Epoch [5] Train loss : [2.27736] Validation loss : [2.34004]
Epoch [6] Train loss : [2.20770] Validation loss : [1.74524]

------------------ Model Saved ------------------
Epoch [7] Train loss : [2.07359] Validation loss : [1.68004]

------------------ Model Saved ------------------
Epoch [8] Train loss : [2.08422] Validation loss : [1.72020]
Epoch [9] Train loss : [2.06862] Validation loss : [2.37194]
Epoch [10] Train loss : [2.04888] Validation loss : [1.54616]

------------------ Model Saved ------------------
Epoch [11] Train loss : [1.98765] Validation loss : [1.53102]

------------------ Model Saved ------------------
Epoch [12] Train loss : [1.89245] Validation loss : [2.19282]
Epoch [13] Train loss : [1.87379] Validation loss : [1.51819]

------------------ Model Saved ------------------
Epoch [14] Train loss : [1.75460] Validation loss : [2.21360]
Epoch [15] Train loss : [1.73565] Validation loss : [1.63400]
Epoch [16] Train loss : [1.59869] Validation loss : [1.97278]
Epoch [17] Train loss : [1.49179] Validation loss : [1.68594]
Epoch [18] Train loss : [1.34463] Validation loss : [1.86969]
Epoch [19] Train loss : [1.36132] Validation loss : [1.22912]

------------------ Model Saved ------------------
Epoch [20] Train loss : [1.21600] Validation loss : [1.14191]

------------------ Model Saved ------------------
Epoch [21] Train loss : [1.16715] Validation loss : [1.10007]

------------------ Model Saved ------------------
Epoch [22] Train loss : [1.11092] Validation loss : [2.50398]
Epoch [23] Train loss : [0.99931] Validation loss : [0.55899]

------------------ Model Saved ------------------
Epoch [24] Train loss : [0.84455] Validation loss : [0.80026]
Epoch [25] Train loss : [0.94551] Validation loss : [1.06891]
Epoch [26] Train loss : [0.81562] Validation loss : [0.50077]

------------------ Model Saved ------------------
Epoch [27] Train loss : [0.68309] Validation loss : [1.37063]
Epoch [28] Train loss : [0.71110] Validation loss : [1.09465]
Epoch [29] Train loss : [0.63951] Validation loss : [0.68203]
Epoch [30] Train loss : [0.58986] Validation loss : [2.68518]
Epoch [31] Train loss : [0.61897] Validation loss : [1.09863]
Epoch [32] Train loss : [0.50844] Validation loss : [0.36524]

------------------ Model Saved ------------------
Epoch [33] Train loss : [0.55933] Validation loss : [0.28480]

------------------ Model Saved ------------------
Epoch [34] Train loss : [0.50001] Validation loss : [0.85017]
Epoch [35] Train loss : [0.47386] Validation loss : [0.51148]
Epoch [36] Train loss : [0.47391] Validation loss : [0.41513]
Epoch [37] Train loss : [0.38743] Validation loss : [1.21229]
Epoch [38] Train loss : [0.42463] Validation loss : [1.67855]
Epoch [39] Train loss : [0.36873] Validation loss : [1.04304]
Epoch [40] Train loss : [0.32091] Validation loss : [0.18763]

------------------ Model Saved ------------------
Epoch [41] Train loss : [0.33197] Validation loss : [0.12528]

------------------ Model Saved ------------------
Epoch [42] Train loss : [0.35905] Validation loss : [0.29721]
Epoch [43] Train loss : [0.28091] Validation loss : [0.07708]

------------------ Model Saved ------------------
Epoch [44] Train loss : [0.35579] Validation loss : [1.34430]
Epoch [45] Train loss : [0.30317] Validation loss : [0.20846]
Epoch [46] Train loss : [0.26936] Validation loss : [0.08450]
Epoch [47] Train loss : [0.24319] Validation loss : [0.15537]
Epoch [48] Train loss : [0.27607] Validation loss : [0.15181]
Epoch [49] Train loss : [0.26515] Validation loss : [0.17000]
Epoch [50] Train loss : [0.24079] Validation loss : [0.29207]

### ResNet50_adam_0.001

model : ResNet50
optimizer : adam, learning rate : 0.001
Epoch [1] Train loss : [1.60612] Validation loss : [1.64180]

------------------ Model Saved ------------------
Epoch [2] Train loss : [0.91744] Validation loss : [0.61422]

------------------ Model Saved ------------------
Epoch [3] Train loss : [0.81058] Validation loss : [0.80247]
Epoch [4] Train loss : [0.55162] Validation loss : [1.07563]
Epoch [5] Train loss : [0.56323] Validation loss : [0.47543]

------------------ Model Saved ------------------
Epoch [6] Train loss : [0.39274] Validation loss : [0.10945]

------------------ Model Saved ------------------
Epoch [7] Train loss : [0.40730] Validation loss : [0.20460]
Epoch [8] Train loss : [0.37551] Validation loss : [0.17822]
Epoch [9] Train loss : [0.32454] Validation loss : [0.13587]
Epoch [10] Train loss : [0.26467] Validation loss : [0.05756]

------------------ Model Saved ------------------
Epoch [11] Train loss : [0.28280] Validation loss : [0.15740]
Epoch [12] Train loss : [0.31475] Validation loss : [0.35838]
Epoch [13] Train loss : [0.29491] Validation loss : [0.25872]
Epoch [14] Train loss : [0.32780] Validation loss : [0.23730]
Epoch [15] Train loss : [0.32922] Validation loss : [0.20376]
Epoch [16] Train loss : [0.21101] Validation loss : [0.12372]
Epoch [17] Train loss : [0.22422] Validation loss : [0.04396]

------------------ Model Saved ------------------
Epoch [18] Train loss : [0.15835] Validation loss : [0.09568]
Epoch [19] Train loss : [0.18439] Validation loss : [0.02356]

------------------ Model Saved ------------------
Epoch [20] Train loss : [0.16493] Validation loss : [0.06998]
Epoch [21] Train loss : [0.17446] Validation loss : [0.04779]
Epoch [22] Train loss : [0.15295] Validation loss : [0.02791]
Epoch [23] Train loss : [0.16958] Validation loss : [0.03460]
Epoch [24] Train loss : [0.13871] Validation loss : [0.03800]
Epoch [25] Train loss : [0.16950] Validation loss : [0.00962]

------------------ Model Saved ------------------
Epoch [26] Train loss : [0.18463] Validation loss : [0.20754]
Epoch [27] Train loss : [0.19758] Validation loss : [0.01947]
Epoch [28] Train loss : [0.14223] Validation loss : [0.03977]
Epoch [29] Train loss : [0.18686] Validation loss : [0.03937]
Epoch [30] Train loss : [0.16624] Validation loss : [0.07273]
Epoch [31] Train loss : [0.11748] Validation loss : [0.01002]
Epoch [32] Train loss : [0.09177] Validation loss : [0.17983]
Epoch [33] Train loss : [0.15055] Validation loss : [0.05779]
Epoch [34] Train loss : [0.11420] Validation loss : [0.01124]
Epoch [35] Train loss : [0.14769] Validation loss : [0.06753]

### ResNet50_rmsprop_0.001

model : ResNet50
optimizer : rmsprop, learning rate : 0.001
Epoch [1] Train loss : [3.35417] Validation loss : [2.39606]

------------------ Model Saved ------------------
Epoch [2] Train loss : [2.52962] Validation loss : [2.32801]

------------------ Model Saved ------------------
Epoch [3] Train loss : [2.45487] Validation loss : [2.01286]

------------------ Model Saved ------------------
Epoch [4] Train loss : [2.27917] Validation loss : [1.81988]

------------------ Model Saved ------------------
Epoch [5] Train loss : [2.04786] Validation loss : [1.80478]

------------------ Model Saved ------------------
Epoch [6] Train loss : [1.88663] Validation loss : [1.47574]

------------------ Model Saved ------------------
Epoch [7] Train loss : [1.90080] Validation loss : [1.46492]

------------------ Model Saved ------------------
Epoch [8] Train loss : [1.69238] Validation loss : [1.98727]
Epoch [9] Train loss : [1.62257] Validation loss : [1.22354]

------------------ Model Saved ------------------
Epoch [10] Train loss : [1.47799] Validation loss : [2.20861]
Epoch [11] Train loss : [1.32850] Validation loss : [1.65192]
Epoch [12] Train loss : [1.17640] Validation loss : [0.78717]

------------------ Model Saved ------------------
Epoch [13] Train loss : [0.98374] Validation loss : [0.60705]

------------------ Model Saved ------------------
Epoch [14] Train loss : [0.96496] Validation loss : [0.56426]

------------------ Model Saved ------------------
Epoch [15] Train loss : [0.84155] Validation loss : [0.66995]
Epoch [16] Train loss : [0.73865] Validation loss : [1.80810]
Epoch [17] Train loss : [0.72031] Validation loss : [0.40449]

------------------ Model Saved ------------------
Epoch [18] Train loss : [0.65213] Validation loss : [0.59535]
Epoch [19] Train loss : [0.67031] Validation loss : [0.84093]
Epoch [20] Train loss : [0.56660] Validation loss : [0.28107]

------------------ Model Saved ------------------
Epoch [21] Train loss : [0.50095] Validation loss : [0.44212]
Epoch [22] Train loss : [0.51197] Validation loss : [1.57999]
Epoch [23] Train loss : [0.48016] Validation loss : [0.24882]

------------------ Model Saved ------------------
Epoch [24] Train loss : [0.37785] Validation loss : [0.14272]

------------------ Model Saved ------------------
Epoch [25] Train loss : [0.43952] Validation loss : [0.15705]
Epoch [26] Train loss : [0.39566] Validation loss : [0.10707]

------------------ Model Saved ------------------
Epoch [27] Train loss : [0.31202] Validation loss : [0.20217]
Epoch [28] Train loss : [0.37781] Validation loss : [0.20109]
Epoch [29] Train loss : [0.41559] Validation loss : [0.19421]
Epoch [30] Train loss : [0.27404] Validation loss : [0.11120]
Epoch [31] Train loss : [0.33405] Validation loss : [0.31247]
Epoch [32] Train loss : [0.31019] Validation loss : [0.09925]

------------------ Model Saved ------------------
Epoch [33] Train loss : [0.29282] Validation loss : [0.87535]
Epoch [34] Train loss : [0.30737] Validation loss : [0.06428]

------------------ Model Saved ------------------
Epoch [35] Train loss : [0.31007] Validation loss : [0.13626]
Epoch [36] Train loss : [0.25789] Validation loss : [1.00369]
Epoch [37] Train loss : [0.25700] Validation loss : [0.16964]
Epoch [38] Train loss : [0.24665] Validation loss : [0.33293]
Epoch [39] Train loss : [0.19152] Validation loss : [0.16407]
Epoch [40] Train loss : [0.25178] Validation loss : [0.65157]
Epoch [41] Train loss : [0.27964] Validation loss : [0.04857]

------------------ Model Saved ------------------
Epoch [42] Train loss : [0.19150] Validation loss : [0.01646]

------------------ Model Saved ------------------
Epoch [43] Train loss : [0.23162] Validation loss : [0.11015]
Epoch [44] Train loss : [0.18209] Validation loss : [0.04323]
Epoch [45] Train loss : [0.21656] Validation loss : [0.08539]
Epoch [46] Train loss : [0.20948] Validation loss : [1.07671]
Epoch [47] Train loss : [0.22202] Validation loss : [0.05338]
Epoch [48] Train loss : [0.25658] Validation loss : [0.04115]
Epoch [49] Train loss : [0.15386] Validation loss : [0.00727]

------------------ Model Saved ------------------
Epoch [50] Train loss : [0.17062] Validation loss : [0.05228]

### ResNet50_nadam_0.001

### ResNet50_adam_0.0001

### ResNet50_rmsprop_0.0001

### ResNet50_nadam_0.0001



# Colab

### ResNet50_adam_0.01

model : ResNet50
optimizer : adam, learning rate : 0.01
Epoch [1] Train loss : [2.07691] Validation loss : [1.50583]

------------------ Model Saved ------------------
Epoch [2] Train loss : [1.29175] Validation loss : [1.15172]

------------------ Model Saved ------------------
Epoch [3] Train loss : [0.94506] Validation loss : [0.69431]

------------------ Model Saved ------------------
Epoch [4] Train loss : [0.75780] Validation loss : [1.07362]
Epoch [5] Train loss : [0.72031] Validation loss : [0.37722]

------------------ Model Saved ------------------
Epoch [6] Train loss : [0.42954] Validation loss : [0.43753]
Epoch [7] Train loss : [0.55043] Validation loss : [0.41045]
Epoch [8] Train loss : [0.37058] Validation loss : [0.37679]

------------------ Model Saved ------------------
Epoch [9] Train loss : [0.40015] Validation loss : [0.22264]

------------------ Model Saved ------------------
Epoch [10] Train loss : [0.31391] Validation loss : [0.19347]

------------------ Model Saved ------------------
Epoch [11] Train loss : [0.25493] Validation loss : [0.15557]

------------------ Model Saved ------------------
Epoch [12] Train loss : [0.28224] Validation loss : [1.81590]
Epoch [13] Train loss : [0.26316] Validation loss : [0.28766]
Epoch [14] Train loss : [0.20224] Validation loss : [0.85871]
Epoch [15] Train loss : [0.24268] Validation loss : [0.17940]
Epoch [16] Train loss : [0.23401] Validation loss : [0.13129]

------------------ Model Saved ------------------
Epoch [17] Train loss : [0.34262] Validation loss : [0.10562]

------------------ Model Saved ------------------
Epoch [18] Train loss : [0.29107] Validation loss : [0.04515]

------------------ Model Saved ------------------
Epoch [19] Train loss : [0.20184] Validation loss : [0.16017]
Epoch [20] Train loss : [0.18055] Validation loss : [0.23258]
Epoch [21] Train loss : [0.22113] Validation loss : [0.04403]

------------------ Model Saved ------------------
Epoch [22] Train loss : [0.12143] Validation loss : [0.72006]
Epoch [23] Train loss : [0.12335] Validation loss : [0.12239]
Epoch [24] Train loss : [0.15035] Validation loss : [0.21607]
Epoch [25] Train loss : [0.18382] Validation loss : [0.40496]
Epoch [26] Train loss : [0.14307] Validation loss : [0.12621]
Epoch [27] Train loss : [0.13799] Validation loss : [4.46157]
Epoch [28] Train loss : [0.13997] Validation loss : [0.14419]
Epoch [29] Train loss : [0.15086] Validation loss : [0.02610]

------------------ Model Saved ------------------
Epoch [30] Train loss : [0.15475] Validation loss : [0.04703]
Epoch [31] Train loss : [0.16258] Validation loss : [0.01637]

------------------ Model Saved ------------------
Epoch [32] Train loss : [0.15085] Validation loss : [0.03201]
Epoch [33] Train loss : [0.12417] Validation loss : [0.15154]
Epoch [34] Train loss : [0.17448] Validation loss : [0.17105]
Epoch [35] Train loss : [0.12421] Validation loss : [0.38754]
Epoch [36] Train loss : [0.12658] Validation loss : [0.04836]
Epoch [37] Train loss : [0.09774] Validation loss : [0.02475]
Epoch [38] Train loss : [0.09108] Validation loss : [0.11299]
Epoch [39] Train loss : [0.09981] Validation loss : [0.01444]

------------------ Model Saved ------------------
Epoch [40] Train loss : [0.10641] Validation loss : [0.02563]
Epoch [41] Train loss : [0.12339] Validation loss : [0.05227]
Epoch [42] Train loss : [0.13196] Validation loss : [0.12270]
Epoch [43] Train loss : [0.10022] Validation loss : [0.16323]
Epoch [44] Train loss : [0.10308] Validation loss : [0.06321]
Epoch [45] Train loss : [0.07279] Validation loss : [0.06107]
Epoch [46] Train loss : [0.10991] Validation loss : [0.87664]
Epoch [47] Train loss : [0.10862] Validation loss : [22.46809]
Epoch [48] Train loss : [0.13930] Validation loss : [0.04180]
Epoch [49] Train loss : [0.10501] Validation loss : [0.08356]

### EfficientNetB4_adam_0.01

model : EfficientNetb4
optimizer : adam, learning rate : 0.01
Epoch [1] Train loss : [1.89697] Validation loss : [4.68389]

------------------ Model Saved ------------------
Epoch [2] Train loss : [0.91442] Validation loss : [2.11622]

------------------ Model Saved ------------------
Epoch [3] Train loss : [0.60557] Validation loss : [0.44224]

------------------ Model Saved ------------------
Epoch [4] Train loss : [0.38615] Validation loss : [0.32063]

------------------ Model Saved ------------------
Epoch [5] Train loss : [0.29617] Validation loss : [0.95255]
Epoch [6] Train loss : [0.28332] Validation loss : [0.10100]

------------------ Model Saved ------------------
Epoch [7] Train loss : [0.22654] Validation loss : [0.21144]
Epoch [8] Train loss : [0.29893] Validation loss : [0.69344]
Epoch [9] Train loss : [0.31003] Validation loss : [0.12993]
Epoch [10] Train loss : [0.21969] Validation loss : [0.38782]
Epoch [11] Train loss : [0.26191] Validation loss : [0.04083]

------------------ Model Saved ------------------
Epoch [12] Train loss : [0.18789] Validation loss : [0.07831]
Epoch [13] Train loss : [0.13910] Validation loss : [0.10673]
Epoch [14] Train loss : [0.08295] Validation loss : [0.03887]

------------------ Model Saved ------------------
Epoch [15] Train loss : [0.08277] Validation loss : [0.08281]
Epoch [16] Train loss : [0.15927] Validation loss : [0.02931]

------------------ Model Saved ------------------
Epoch [17] Train loss : [0.21852] Validation loss : [0.78872]
Epoch [18] Train loss : [0.22195] Validation loss : [0.17590]
Epoch [19] Train loss : [0.26994] Validation loss : [0.60365]
Epoch [20] Train loss : [0.23647] Validation loss : [0.06064]
Epoch [21] Train loss : [0.12625] Validation loss : [0.01968]

------------------ Model Saved ------------------
Epoch [22] Train loss : [0.08420] Validation loss : [0.01654]

------------------ Model Saved ------------------
Epoch [23] Train loss : [0.13281] Validation loss : [0.06808]
Epoch [24] Train loss : [0.18296] Validation loss : [0.09007]
Epoch [25] Train loss : [0.13878] Validation loss : [0.17522]
Epoch [26] Train loss : [0.11493] Validation loss : [0.01604]

------------------ Model Saved ------------------
Epoch [27] Train loss : [0.08333] Validation loss : [0.00502]

------------------ Model Saved ------------------
Epoch [28] Train loss : [0.05048] Validation loss : [0.00714]
Epoch [29] Train loss : [0.04940] Validation loss : [0.01809]
Epoch [30] Train loss : [0.11036] Validation loss : [0.01142]
Epoch [31] Train loss : [0.08243] Validation loss : [0.03819]
Epoch [32] Train loss : [0.13286] Validation loss : [0.00851]
Epoch [33] Train loss : [0.09916] Validation loss : [0.08450]
Epoch [34] Train loss : [0.12744] Validation loss : [0.13571]
Epoch [35] Train loss : [0.15554] Validation loss : [0.04044]
Epoch [36] Train loss : [0.08070] Validation loss : [0.08916]
Epoch [37] Train loss : [0.11283] Validation loss : [0.20141]

### EfficientNetb4_rmsprop_0.01

model : EfficientNetb4
optimizer : rmsprop, learning rate : 0.01
Epoch [1] Train loss : [16.41693] Validation loss : [6.49829]

------------------ Model Saved ------------------
Epoch [2] Train loss : [3.93759] Validation loss : [2.80680]

------------------ Model Saved ------------------
Epoch [3] Train loss : [2.57483] Validation loss : [2.18103]

------------------ Model Saved ------------------
Epoch [4] Train loss : [2.02991] Validation loss : [21.91300]
Epoch [5] Train loss : [1.66463] Validation loss : [1.20073]

------------------ Model Saved ------------------
Epoch [6] Train loss : [1.35434] Validation loss : [0.93361]

------------------ Model Saved ------------------
Epoch [7] Train loss : [2.14836] Validation loss : [1.72735]
Epoch [8] Train loss : [1.15302] Validation loss : [1.76601]
Epoch [9] Train loss : [0.96608] Validation loss : [0.65510]

------------------ Model Saved ------------------
Epoch [10] Train loss : [0.81410] Validation loss : [0.66957]
Epoch [11] Train loss : [0.93451] Validation loss : [0.41283]

------------------ Model Saved ------------------
Epoch [12] Train loss : [0.61766] Validation loss : [1.43316]
Epoch [13] Train loss : [0.87440] Validation loss : [0.57543]
Epoch [14] Train loss : [0.62522] Validation loss : [0.43959]
Epoch [15] Train loss : [1.25748] Validation loss : [0.43395]
Epoch [16] Train loss : [0.38057] Validation loss : [0.26378]

------------------ Model Saved ------------------
Epoch [17] Train loss : [0.39177] Validation loss : [0.23283]

------------------ Model Saved ------------------
Epoch [18] Train loss : [0.36418] Validation loss : [0.11417]

------------------ Model Saved ------------------
Epoch [19] Train loss : [2.77444] Validation loss : [1.61719]
Epoch [20] Train loss : [0.65614] Validation loss : [0.25599]
Epoch [21] Train loss : [0.39216] Validation loss : [0.10140]

------------------ Model Saved ------------------
Epoch [22] Train loss : [0.37509] Validation loss : [0.83130]
Epoch [23] Train loss : [0.36227] Validation loss : [0.07629]

------------------ Model Saved ------------------
Epoch [24] Train loss : [0.24851] Validation loss : [0.77365]
Epoch [25] Train loss : [0.35790] Validation loss : [1.01861]
Epoch [26] Train loss : [0.34944] Validation loss : [0.17645]
Epoch [27] Train loss : [0.27853] Validation loss : [0.22879]
Epoch [28] Train loss : [0.30335] Validation loss : [0.06236]

------------------ Model Saved ------------------
Epoch [29] Train loss : [1.38105] Validation loss : [0.17211]
Epoch [30] Train loss : [0.17917] Validation loss : [0.05237]

------------------ Model Saved ------------------
Epoch [31] Train loss : [0.20941] Validation loss : [0.42043]
Epoch [32] Train loss : [0.19138] Validation loss : [0.09381]
Epoch [33] Train loss : [0.20570] Validation loss : [0.04724]

------------------ Model Saved ------------------
Epoch [34] Train loss : [0.16065] Validation loss : [0.04014]

------------------ Model Saved ------------------
Epoch [35] Train loss : [0.35239] Validation loss : [0.76807]
Epoch [36] Train loss : [0.25001] Validation loss : [0.68073]
Epoch [37] Train loss : [0.35976] Validation loss : [0.04149]
Epoch [38] Train loss : [0.16142] Validation loss : [0.08942]
Epoch [39] Train loss : [0.18558] Validation loss : [0.16551]
Epoch [40] Train loss : [0.17803] Validation loss : [0.13476]
Epoch [41] Train loss : [0.27275] Validation loss : [0.10605]
Epoch [42] Train loss : [0.16338] Validation loss : [0.39066]
Epoch [43] Train loss : [0.12914] Validation loss : [0.10276]
Epoch [44] Train loss : [1.23465] Validation loss : [0.09415]

### EfficientNetb4_nadam_0.01

