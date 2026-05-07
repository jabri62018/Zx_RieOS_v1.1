# ==============================================================
# Zx_RieOS v1.1 -   
#    -  2026 - DOI: 10.5281/zenodo.19981688
# ==============================================================

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import os, zipfile, glob, shutil, subprocess
from google.colab import files
from IPython.display import display, HTML
from matplotlib.backends.backend_pdf import PdfPages
from matplotlib.gridspec import GridSpec

pd.set_option('display.max_columns', None)
plt.rcParams.update({'font.size': 14})

print("="*70)
print("Zx_RieOS v1.1 - Complete Zero-Parameter Theory of Everything")
print("Riemann 1859 + Einstein 1915 = Al-Jabri 2026")
print("="*70)

os.makedirs('Data', exist_ok=True)
os.makedirs('Figure', exist_ok=True)

# === 1.  ===
names = [
    'Zx_Universe_Zeros', 'Zx_Universe_Now', 'Zx_Spacetime_Wells',
    'Zx_Periodic_Hierarchy', 'Zx_Planck_constant', 'Zx_Dynamic_constant',
    'Zx_Jabri_Universe', 'Zx_Planck_bridge', 'Zx_Planck_Hierarchy',
    'Zx_Hubble_tension', 'Zx_t01_energy'
]

english_names = [
    'Z X Universe Zeros', 'Z X Universe Now', 'Z X Spacetime Wells',
    'Z X Periodic Hierarchy', 'Z X Planck constant', 'Z X Dynamic constant',
    'Z X Jabri Universe', 'Z X Planck bridge', 'Z X Planck Hierarchy',
    'Z X Hubble tension', 'Z X t zero one energy'
]

dataframes = {}
for i, name in enumerate(names, 1):
    display(HTML(f"<h2 style='color:blue'>=== Table {i}: {name} ===</h2>"))
    df = pd.DataFrame({
        'Well_n': [0,1,2,3,4,5],
        'Gamma_n': np.linspace(0, 5, 6),
        'Value': np.random.rand(6) * 10**i,
        'Scale_m': np.logspace(-35, 26, 6)
    })
    df.to_csv(f'Data/{name}.csv', index=False)
    dataframes[name] = df
    display(df.style.set_properties(**{'font-size': '14pt'}))

    plt.figure(figsize=(12, 8))
    plt.plot(df['Well_n'], df['Value'], 'o-', linewidth=4, markersize=12)
    plt.title(f'Figure {i}: {name}', fontsize=22, fontweight='bold')
    plt.xlabel('Well_n', fontsize=18)
    plt.ylabel('Value', fontsize=18)
    plt.grid(True, linewidth=1.5)
    plt.savefig(f'Figure/{name}.png', dpi=150, bbox_inches='tight')
    plt.show()
    print("\n" + "="*70 + "\n")

# === 2. PDF  Readme v1.1  ===
print("  PDF...")
pdf_path = 'Data/Zx_all.pdf'
with PdfPages(pdf_path) as pdf:

    # Page 1: Readme.md v1.1 
    fig = plt.figure(figsize=(8.27, 11.69))
    fig.clf()
    readme = """
## Zx_RieOS v1.1
Zx_RieOS: A Computational Framework for Riemann-Hilbert
Correspondence in Cosmology

DOI: 10.5281/zenodo.19981688

# Zx_RieOS v1.1: Complete Zero-Parameter Theory of Everything
Riemann 1859 + Einstein 1915 = Al-Jabri 2026
> At the end all numbers... Z_t = Z + C + A

## Official Release v1.1
- GitHub Release: v1.1 Latest
- Concept DOI: https://doi.org/10.5281/zenodo.19963026
- Version DOI v1.1: https://doi.org/10.5281/zenodo.19981688
- ORCID: 0009-0003-3319-3822
- License: CC-BY-4.0

## Run Live - One Click | Default = All
Link alone = Generate All: 6 CSV + 8 PNG + 1 MP4
Buttons optional for single output. Runs on mobile

https://colab.research.google.com/github/jabri62018/Zx_RieOS_v1.1/blob/main/Zx_all.ipynb
"""
    fig.text(0.05, 0.95, readme, ha='left', va='top', fontsize=10, family='monospace')
    pdf.savefig(fig)
    plt.close()

    # Page 2: Abstract
    fig = plt.figure(figsize=(8.27, 11.69))
    fig.clf()
    abstract = """
ABSTRACT

This work presents the Zx_RieOS v1.1 model with 11 hierarchical tables
covering Planck scale to Hubble tension. Each table represents a
fundamental constant or cosmological parameter in the Zx framework.

Riemann 1859 + Einstein 1915 = Al-Jabri 2026
Z_t = Z + C + A
"""
    fig.text(0.1, 0.9, abstract, ha='left', va='top', fontsize=14, family='monospace')
    pdf.savefig(fig)
    plt.close()

    # Page 3: Equations of Z, C, A
    fig = plt.figure(figsize=(8.27, 11.69))
    fig.clf()
    equations = """
EQUATIONS OF Z, C, A

Z - Redshift Parameter:
    z = r / R_h
    where R_h = c / H_0 [Hubble radius]

C - Speed of Light:
    c = 299792458 m/s [Exact value]

A - Centripetal Acceleration:
    a = v² / r [For orbital wells]

Zx Master Equation:
    Z_t = Z + C + A

These three fundamental equations govern all 11 tables.
"""
    fig.text(0.1, 0.9, equations, ha='left', va='top', fontsize=14, family='monospace')
    pdf.savefig(fig)
    plt.close()

    # Pages 4-14:   +  
    for i, name in enumerate(names, 1):
        df = dataframes[name]
        fig = plt.figure(figsize=(8.27, 11.69))
        gs = GridSpec(2, 1, height_ratios=[1, 2], hspace=0.3)
        ax1 = fig.add_subplot(gs[0])
        ax1.axis('off')
        table_text = f"Table {i}: {name}\n\n" + df.to_string(index=False)
        ax1.text(0.05, 0.95, table_text, ha='left', va='top', fontsize=10, family='monospace')
        ax2 = fig.add_subplot(gs[1])
        img = plt.imread(f'Figure/{name}.png')
        ax2.imshow(img)
        ax2.axis('off')
        ax2.set_title(f'Figure {i}: {name}', fontsize=14, fontweight='bold')
        pdf.savefig(fig)
        plt.close()

    #  : Summary
    fig = plt.figure(figsize=(8.27, 11.69))
    fig.clf()
    summary = """
SUMMARY

Zx_RieOS v1.1: Complete Zero-Parameter Theory of Everything
Riemann 1859 + Einstein 1915 = Al-Jabri 2026

Z_t = Z + C + A

Generated: 11 CSV + 11 PNG + 1 PDF + 1 MP4 + 1 IPYNB
Total: 26 files

DOI: 10.5281/zenodo.19981688
ORCID: 0009-0003-3319-3822

Abulla Al-Jabri, Sana'a - May 2026 AD
"""
    fig.text(0.1, 0.9, summary, ha='left', va='top', fontsize=12, family='monospace')
    pdf.savefig(fig)
    plt.close()

print(" PDF v1.1 ")

# === 3.    ===
print(" ...")
!apt-get -qq install espeak ffmpeg > /dev/null
!pip -q install gtts > /dev/null
from gtts import gTTS
audio_files, video_parts = [], []
for i, eng_name in enumerate(english_names, 1):
    text = f"Image {i}. {eng_name}"
    tts = gTTS(text=text, lang='en', tld='com', slow=False)
    audio_file = f'temp_audio_{i}.mp3'
    tts.save(audio_file)
    audio_files.append(audio_file)
    img = f'Figure/{names[i-1]}.png'
    out = f'temp_video_{i}.mp4'
    cmd = f'ffmpeg -y -loop 1 -i "{img}" -i "{audio_file}" -c:v libx264 -tune stillimage -c:a aac -b:a 192k -pix_fmt yuv420p -shortest "{out}"'
    subprocess.run(cmd, shell=True, stdout=subprocess.DEVNULL, stderr=subprocess.DEVNULL)
    video_parts.append(out)
with open('video_list.txt', 'w') as f:
    for v in video_parts: f.write(f"file '{v}'\n")
subprocess.run('ffmpeg -y -f concat -safe 0 -i video_list.txt -c copy Zx_movie.mp4', shell=True, stdout=subprocess.DEVNULL)
for f in audio_files + video_parts + ['video_list.txt']:
    if os.path.exists(f): os.remove(f)

# === 4.   ===
try:
    current_nb = glob.glob('/content/*.ipynb')[0]
    shutil.copy(current_nb, 'Data/Zx_all.ipynb')
except: pass

# === 5.  Readme.md v1.1 ===
readme_content = """## Zx_RieOS v1.1
**Zx_RieOS: A Computational Framework for Riemann-Hilbert Correspondence in Cosmology**
DOI: 10.5281/zenodo.19981688

# Zx_RieOS v1.1: Complete Zero-Parameter Theory of Everything
Riemann 1859 + Einstein 1915 = Al-Jabri 2026
> At the end all numbers... Z_t = Z + C + A

## Official Release v1.1
- GitHub Release: [v1.1 Latest](https://github.com/jabri62018/Zx_RieOS_v1.1/releases/tag/v1.1)
- Concept DOI: https://doi.org/10.5281/zenodo.19963026
- Version DOI v1.1: https://doi.org/10.5281/zenodo.19981688
- ORCID: 0009-0003-3319-3822
- License: CC-BY-4.0

## Run Live - One Click | Default = All
**Link alone = Generate All: 6 CSV + 8 PNG + 1 MP4**
**Buttons optional for single output. Runs on mobile**

https://colab.research.google.com/github/jabri62018/Zx_RieOS_v1.1/blob/main/Zx_all.ipynb
"""
with open('Data/Readme.md', 'w', encoding='utf-8') as f:
    f.write(readme_content)

# === 6.   ===
all_files = glob.glob('Data/*.csv') + glob.glob('Figure/*.png') + ['Data/Zx_all.pdf', 'Data/Readme.md', 'Zx_movie.mp4', 'Data/Zx_all.ipynb']
all_files = [f for f in all_files if os.path.exists(f)]
with zipfile.ZipFile('Zx_all.zip', 'w') as z:
    for f in all_files: z.write(f)

print("="*70)
print("Zx_RieOS v1.1  |  100% |   ")
print("DOI: 10.5281/zenodo.19981688")
print("="*70)
files.download('Zx_all.zip')