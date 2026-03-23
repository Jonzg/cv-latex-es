# CV LaTeX - Jon Zorrilla Gamboa

Curriculum vitae en español generado con LaTeX. Utiliza una clase personalizada (`simplecv.sty`) con soporte para bibliografía en formato IEEE, iconos, hipervínculos y diseño en dos columnas.

## Estructura del proyecto

```
CV_jz_es/
├── main.tex              # Documento principal
├── simplecv.sty          # Estilo/clase personalizada del CV
├── papers.bib            # Referencias bibliográficas (BibTeX)
└── sections/
    ├── experience.tex
    ├── education.tex
    ├── courses.tex
    ├── skills.tex
    ├── languages.tex
    ├── publications.tex
    ├── teaching.tex
    ├── projects.tex
    ├── awards.tex
    └── extracurricular.tex
```

El archivo `main.tex` importa las secciones necesarias con `\import`. Las secciones comentadas en `main.tex` están disponibles pero no se incluyen en la compilación actual.

## Clonar el repositorio

```bash
git clone git@github.com:Jonzg/cv-latex-es.git
cd cv-latex-es
```

## Preparar entorno en WSL (Ubuntu/Debian)

### 1. Actualizar paquetes del sistema

```bash
sudo apt update && sudo apt upgrade -y
```

### 2. Instalar TeX Live y herramientas necesarias

```bash
sudo apt install -y \
    texlive-latex-base \
    texlive-latex-extra \
    texlive-latex-recommended \
    texlive-fonts-recommended \
    texlive-fonts-extra \
    texlive-bibtex-extra \
    texlive-lang-cyrillic \
    biber \
    latexmk
```

> `texlive-fonts-extra` incluye `fontawesome5`.
> `texlive-lang-cyrillic` proporciona soporte para `babel` con el idioma ruso (requerido por `simplecv.sty`).
> `biber` es el backend de `biblatex` para gestionar la bibliografía.
> `latexmk` automatiza el proceso de compilación con múltiples pasadas.

### 3. (Opcional) Instalar un editor LaTeX

Para editar con interfaz gráfica dentro de WSL con soporte X11 o WSLg:

```bash
sudo apt install -y texstudio
```

O usar VS Code con la extensión **LaTeX Workshop** desde Windows apuntando al directorio WSL.

## Compilar el CV

Con `latexmk` (recomendado, gestiona automáticamente las pasadas de BibTeX/Biber):

```bash
latexmk -pdf -interaction=nonstopmode main.tex
```

El PDF resultante se genera como `main.pdf`.

Para limpiar los archivos auxiliares:

```bash
latexmk -c
```

### Compilación manual (alternativa)

```bash
pdflatex main.tex
biber main
pdflatex main.tex
pdflatex main.tex
```

## Personalización

- **Color del tema:** modificar `\def\theme{MidnightBlue}` en `main.tex` por cualquier color predefinido de `xcolor` (ej. `RedViolet`, `ForestGreen`, `black`).
- **Secciones activas:** comentar/descomentar los `\import{sections/}{...}` en `main.tex`.
- **Bibliografía:** añadir entradas en `papers.bib`; la sección `publications.tex` las renderiza automáticamente.
