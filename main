import streamlit as st
import matplotlib.pyplot as plt

st.set_page_config(layout="wide")


lista_fc = [210, 280, 350, 420, 560]

aceros = {
    "3/8": 0.95,
    "1/2": 1.27,
    "5/8": 1.59,
    "3/4": 1.91,
    "1": 2.54,
    "1-3/8": 3.49
}

"---"

c1,c2 = st.columns([1,4])
with c1: "Diámetro"
with c2: diam = st.pills("Diámetro de varilla:", options=aceros, label_visibility="collapsed", selection_mode="single", default="3/4")

"---"

c1,c2 = st.columns([1,4])
with c1: "f'c"
with c2: fc = st.pills("f'c:", options=lista_fc, label_visibility="collapsed", selection_mode="single", default=280)

"---"


d = aceros[diam]

factor = 2.1 if diam == "1" or diam == "1-3/8" else 2.6

ld_sup = round(4200 * 1.3 * 1 * 1 * d / (factor * (fc*9.81)**0.5))
ld_inf = round(4200 * 1.0 * 1 * 1 * d / (factor * (fc*9.81)**0.5))
ldg = max(round(0.24 * 4200 * d / ((fc*9.81)**0.5)),min(15,8*d))

c1,c2 = st.columns([2.7,2])

fig, ax = plt.subplots(1,1,figsize=(10,4), dpi=250)

ax.fill_between([0,150,150,350],[45,45,90,90], [0,0,-50,-50], color='gray', alpha=0.4)


ax.plot([0,150,150],[0,0,-50], lw=3, color='k')
ax.plot([0,150,150],[45,45,90], lw=3, color='k')

ax.plot([-5,150+ld_sup],[39,39], lw=2, color='m')
ax.plot([-5,150+ld_inf],[5,5], lw=2, color='b')

ax.plot([150,150+ld_sup],[55,55], color='g', lw=2)
ax.plot([150,150],[53,57], color='g', lw=2)
ax.plot([150+ld_sup,150+ld_sup],[53,57], color='g', lw=2)
ax.text(150+ld_sup*0.5,55,f"{ld_sup} cm", ha="center", va="bottom", color='k')


ax.plot([150,150+ld_inf],[-10,-10], color='g', lw=2)
ax.plot([150,150],[-12,-8], color='g', lw=2)
ax.plot([150+ld_inf,150+ld_inf],[-12,-8], color='g', lw=2)
ax.text(150+ld_inf*0.5,-11,f"{ld_inf} cm", ha="center", va="top", color='k')


ax.set_xlim(100,350)
ax.set_ylim(-45,90)
ax.set_xticks([])
ax.set_yticks([])
ax.set_aspect("equal")

with c1: st.pyplot(fig)


fig, ax = plt.subplots(1,1,figsize=(10,4), dpi=250)

ax.fill_between([0,150,150,350],[45,45,90,90], [0,0,-50,-50], color='gray', alpha=0.4)


ax.plot([0,150,150],[0,0,-50], lw=3, color='k')
ax.plot([0,150,150],[45,45,90], lw=3, color='k')

ax.plot([-5,150+ldg,150+ldg],[5,5,5+12*d], lw=2, color='b')


ax.plot([170+ldg,170+ldg],[5,5+12*d], color='g', lw=2)
ax.plot([172+ldg,168+ldg],[5,5], color='g', lw=2)
ax.plot([172+ldg,168+ldg],[5+12*d,5+12*d], color='g', lw=2)
ax.text(175+ldg,5+6*d,f"{12*d:.0f} cm", ha="left", va="center", color='k')

ax.plot([150,150+ldg],[-10,-10], color='g', lw=2)
ax.plot([150,150],[-12,-8], color='g', lw=2)
ax.plot([150+ldg,150+ldg],[-12,-8], color='g', lw=2)
ax.text(150+ldg*0.5,-12,f"{ldg} cm", ha="center", va="top", color='k')



ax.set_xlim(100,280)
ax.set_ylim(-45,90)
ax.set_xticks([])
ax.set_yticks([])
ax.set_aspect("equal")

with c2: st.pyplot(fig)
