![Image](https://raw.githubusercontent.com/vertingo/Easy_Admin_YouTube_Newsletter_Firebase/master/web/assets/images/github/vertin_go_website.jpg)
### 🌐 Apporter votre soutien au projet :heart: pour de futures évolutions!
[![GitHub stars](https://img.shields.io/github/stars/vertingo/screenshott.svg?style=social&label=Star)](https://github.com/vertingo/Anaconda_Videos_Tutos) [![GitHub forks](https://img.shields.io/github/forks/vertingo/screenshott.svg?style=social&label=Fork)](https://github.com/vertingo/Anaconda_Videos_Tutos/fork) [![GitHub watchers](https://img.shields.io/github/watchers/vertingo/screenshott.svg?style=social&label=Watch)](https://github.com/vertingo/Anaconda_Videos_Tutos) [![GitHub followers](https://img.shields.io/github/followers/vertingo.svg?style=social&label=Follow)](https://github.com/vertingo)
[![Twitter Follow](https://img.shields.io/twitter/follow/Vertin_Go.svg?style=social)](https://twitter.com/Vertin_Go)

### 🌐 Anaconda Project

# 🌐 Partie 1: Créer un projet Anaconda et ajouter des sections au anaconda-project.yml

Prérequies Anaconda CLI(https://www.anaconda.com/download/)

### 🌐 Créer un projet Anaconda

```
anaconda-project init (Créer le fichier anaconda-project.yml) ou anaconda-project init --directory directory-name 
(Créer le dossier directory-name et créer dans ce dernier le anaconda-project.yml!)

anaconda-project lock (Pour créer le anaconda-project-lock.yml si celui ci n'éxiste pas!)
```

### 🌐 Lancer un projet Anaconda

```
anaconda-project run

anaconda-project run command-name (Lance la commande command-name spécifié dans le anaconda-project.yml! 
Si aucune )
```

### 🌐 Ajouter une commande

```
anaconda-project add-command name "command"

anaconda-project add-command notebook_test.ipynb

anaconda-project add-command plot app-path-filename

anaconda-project add-command hello "python hello.py"  
(Ajoute la commande hello qui éxecute le fichier hello.py. Si démandé spécifié avec A, B, ou C 
si il s'agit d'une Bokeh app, d'un NoteBook, ou d'une Commande!)
    
anaconda-project add-command upload_notebook "anaconda upload test_notebook.ipynb"

anaconda-project run hello
	
anaconda-project run upload_notebook (Lance la commande précèdement ajouté!)

anaconda-project list-commands (Permet de lister l'ensemble des commandes du fichier anaconda-project.yml!)
```

### 🌐 Ajouter un package

```
anaconda-project add-packages bokeh=0.12 pandas
```
Retrouver tous vos packages sur le chemin suivant: C:\Users\nom_d_utilisateur\AppData\Roaming\Python\Python37\site-packages

### 🌐 Ajouter un env-spec

```
anaconda-project add-env-spec
```

### 🌐 Ajouter une variable

```
anaconda-project add-variable VARIABLE_encrypt-flag (Create an encrypted variable!)

anaconda-project add-variable DB_PASSWORD

anaconda-project add-variable --default=default_value VARIABLE 
(Avec l'option default la variable n'est pas demandé d'être renseigné par l'utilisateur sous forme d'input!)

anaconda-project add-variable --default=petal_width COLUMN_TO_SHOW

anaconda-project unset-variable VARIABLE (Restaure la valeur par défaut!)

anaconda-project set-variable VARIABLE=value (Change la valeur de la variable VARIABLE)
```

### 🌐 Ajouter un service

```
anaconda-project add-service redis
```

### 🌐 Ajouter un download

```
anaconda-project add-download IRIS_CSV 
https://raw.githubusercontent.com/bokeh/bokeh/f9aa6a8caae8c7c12efd32be95ec7b0216f62203/bokeh/sampledata/iris.csv
```

### 🌐 Ajouter une archive

```
anaconda-project archive filename.zip
```

### 🌐 Clean projet

```
anaconda-project clean
```

# 🌐 Partie 2: Upload a Package, Project, Notebook et Environnement

### 🌐 Upload a Package

```
conda install anaconda-client conda-build

git clone https://github.com/Anaconda-Platform/anaconda-client

cd anaconda-client/example-packages/conda/ 
(Contient un fichier build.sh, bld.bat, meta.yaml! 
Pour builder la version archivé du package build.sh pour Linux et bld.bat pour Windows!)

conda config --set anaconda_upload no
conda build .    (Tous les packages build de cette façon sont placés dans un dossier: conda-bld) 
ou 
conda build . --output (-- output permet de connaître l'emplacement du build)

anaconda login
anaconda upload /path/to/conda-package.tar.bz2
```

### 🌐 Upload a Project

```
anaconda-project upload 
(Taper simplement cette commande depuis le dossier racine de votre projet)
```

### 🌐 Upload a NoteBook

```
anaconda upload nom_de_votre_notebook.ipynb 
(Taper cette commande avec le nom de votre notebook au format ipynb)
```

### 🌐 Upload an Environnement

```
conda env export -n my-environment -f my-environment.yml   (Créer un environnement)

anaconda upload my-environment.yml
```

# 🌐 Jupyter NoteBookApp, Generation Docs, et OMDBAPP Partie 3: 

### 🌐 NoteBookApp

```
jupyter notebook --generate-config 
(Génére le fichier de configuration dans le répertoire C:\Users\nom_utilisateur\.jupyter)
```

Décommenter au moins les lignes suivantes dans C:\Users\tedal\.jupyter\jupyter_notebook_config.py

c.NotebookApp.certfile = u'/absolute/path/to/your/certificate/mycert.pem'

c.NotebookApp.keyfile = u'/absolute/path/to/your/certificate/mykey.key'

c.NotebookApp.ip = '*'

c.NotebookApp.password = u'sha1:bcd259ccf...<your hashed password here>'
	
c.NotebookApp.open_browser = False 

c.NotebookApp.port = 9999

```
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout mykey.key -out mycert.pem
(Si vous téléchargé OpenSSL n'oublié pas d'ajouter à la variable d'environnement PATH
le path: C:\OpenSSL\bin dans Panneau de configuration\Système et sécurité\Système 
Paramètre système avancés variables d'environnement.
Une fois la commande exécuté vous obtiendrez les fichiers de certificats mykey.key
et mycert.pem dans le dossier courant ou vous aurez exécuté la commande. Après il vous 
faudra renseigner l'emplacement de ces deux fichiers dans le jupyter_notebook_config.py
dans les variables c.NotebookApp.certfile, c.NotebookApp.keyfile illustré ci-dessus!)


jupyter notebook --certfile=mycert.pem --keyfile mykey.key 
(Sécurise la connexion avec un protocole de cummunication SSL)

jupyter notebook password

jupyter notebook 
(Lancer le notebook dans le serveur, éditer un Notebook, lance une invite de commande, installer IPython)

anaconda upload nom_de_votre_notebook.ipynb (Pour upload un Notebook!)
```

### 🌐 IPython

```
pip install ipyparallel

ipcluster nbextension enable

ipython --matplotlib 
(Aprés cette commande si vous avez des erreurs d'imports, désinstaller les packages 
et réinstaller les par exemple pip uninstall numpy, et ensuite pip install numpy)

run pidigits.py

In [7]: import sympy

In [8]: pi = sympy.pi.evalf(40)

In [9]: pi
Out[9]: 3.141592653589793238462643383279502884197

In [10]: pi = sympy.pi.evalf(10000)

In [11]: digits = (d for d in str(pi)[2:])  # create a sequence of digits

In [13]: freqs = one_digit_freqs(digits)

In [14]: plot_one_digit_freqs(freqs)
Out[14]: [<matplotlib.lines.Line2D object at 0x18a55290>]
```

### 🌐 Insertion dans un NoteBook:

```
import sympy
import numpy as np
from matplotlib import pyplot as plt

normalize=False

digits = (d for d in str(pi)[2:])

freqs = np.zeros(10, dtype='i4')

for d in digits:

    freqs[int(d)] += 1

if normalize:

    freqs = freqs/freqs.sum()
    
ax = plt.plot(freqs,'bo-')

plt.title('Single digit counts in pi')

plt.xlabel('Digit')

plt.ylabel('Count')
```

### 🌐 Génération de la doc
```
conda env create 
(Créer l'environnement d'éxécution à partir du fichier environnement.yml)

source activate anaconda-project-docs

make html

open build/html/index.html
```

### 🌐 OMDBApp

```
anaconda-project run

anaconda-project add-env-spec -n/--dev
```
# MPI

Télécharger l'exécutable suivant et lancer l'installation
(Les 2 options dépendent des spécificités de votre environnement!
Si l'un ne fonctionne pas tester les deux): 
https://www.microsoft.com/en-us/download/details.aspx?id=54607
ou
https://www.microsoft.com/en-us/download/details.aspx?id=47259

Ajouter le chemin suivant à la variable path de votre environnement 
dans le menu:
Panneau de configuration\Système et sécurité\Système 
et 
Paramètres Systèmes avancés -> Variables Environnements: 

C:\Program Files (x86)\Microsoft SDKs\MPI
ou
C:\Program Files\Microsoft MPI\Bin 

```
pip install mpi4py
```

Tester avec un petit programme:

```
from mpi4py import MPI
comm = MPI.COMM_WORLD
rank = comm.Get_rank()
print ('hello world from process ', rank)
```

Si le programme ne fonctionne pas correctement soit mpi4py 
(module could not be found) ou dll 
(DLL load failed: The specified module could not be found)
Assurez-vous d'avoir bien testé les deux liens d'installations
ci-dessus et d'avoir bien renseignés les variables 
d'environnements!

```
ipython profile create --parallel --profile=mpi
```

Editer ~/.ipython/profile_mpi/ipcluster_config.py 
décommenter et modifier:
c.IPClusterEngines.engine_launcher_class = 'MPIEngineSetLauncher'

```
ipcluster start --profile=mpi -n 4
```

```
Un petit coup de pouce suivez nous sur YouTube et Facebook!
[You Tube] ==> https://www.youtube.com/channel/UC2g_-ipVjit6ZlACPWG4JvA?sub_confirmation=1 
[Facebook] ==> https://www.facebook.com/vertingo/ 
```
  
<p align="center">
  <a href="https://www.youtube.com/channel/UC2g_-ipVjit6ZlACPWG4JvA?sub_confirmation=1"><img src="https://platform-media.herokuapp.com/assets/images/reseaux-sociaux/youtube2.png" width="400" height="250"/></a>
  <a href="https://www.facebook.com/vertingo/"><img src="https://platform-media.herokuapp.com/assets/images/reseaux-sociaux/rejoins_nous.png" width="400" height="250"/></a>
</p>
