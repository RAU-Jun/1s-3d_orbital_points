# 수소 원자 오비탈 확률 밀도 시각화 (1s ~ 3d)

수소 원자의 파동함수 ψ로 확률 밀도 |ψ|²를 계산하고, **몬테카를로 샘플링**으로 점을 찍어
1s, 2s, 2p, 3s, 3p, 3d 오비탈의 모양을 3D로 시각화했습니다.

- 언어/라이브러리: Python, NumPy, Matplotlib
- Claude AI는 github 정리에만 사용, 코드 작성에는 미사용함.

```
Chemistry/
  1s_orbital_point.py  2s_orbital_point.py  2p_orbital_point.py
  3s_orbital_point.py  3p_orbital_point.py  3d_orbital_point.py
result/                 # 오비탈별 3D 산점도
```

## 방법

1. 구좌표 (r, θ, φ)를 무작위로 10만 개 뽑습니다.
2. 각 점에서 파동함수(방사 부분 × 각도 부분)로 확률 밀도 |ψ|²를 계산합니다.
3. 0~1 난수가 `|ψ|² / max(|ψ|²)` 보다 작은 점만 남깁니다 (기각 샘플링).
4. 남은 점을 직교좌표로 바꿔 3D 산점도로 그립니다.

3d 오비탈은 각도 부분을 바꿔 d_z², d_xy, d_xz, d_yz, d_x²−y² 다섯 가지를 모두 그립니다.

## 결과

| 1s | 2s | 2p |
|---|---|---|
| ![](result/1s.png) | ![](result/2s.png) | ![](result/2p.png) |

| 3s | 3p | 3d_z² |
|---|---|---|
| ![](result/3s.png) | ![](result/3p.png) | ![](result/3d_z2.png) |

| 3d_xy | 3d_xz | 3d_yz | 3d_x²−y² |
|---|---|---|---|
| ![](result/3d_xy.png) | ![](result/3d_xz.png) | ![](result/3d_yz.png) | ![](result/3d_x2-y2.png) |

## 실행 방법

```bash
pip install numpy matplotlib
python Chemistry/3d_orbital_point.py
```
