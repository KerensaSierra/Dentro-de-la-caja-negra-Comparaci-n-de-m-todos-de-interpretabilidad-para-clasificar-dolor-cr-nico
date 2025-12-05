Autora: Kerensa Soery Sierra Trujillo
Contacto: A01642230@tec.mx
Universidad: Instituto Tecnológico de Monterrey Campus Guadalajara 
#--------------------------

Nombre del proyecto: 
Inside the Black Box-Comparing Interpretability Methods in an AI Model for Chronic Pain Scenario 
#--------------------------

Descripción general del proyecto:
Este trabajo aborda el reto de identificar estados de dolor crónico a partir de volúmenes fMRI de rata mediante redes neuronales convolucionales. El proyecto extiende el estudio previo de Alan Macías, quien empleó un modelo VGG16 3D para clasificar cinco estados de dolor, incorporando ahora un análisis más amplio y comparativo de métodos de interpretabilidad. Además del método base Grad-CAM, se integraron Grad-CAM++, Respond-CAM y HiResCAM con el propósito de fortalecer la comprensión de las regiones cerebrales que contribuyen a la predicción del modelo.
Dado que algunos mapas de activación presentan señales fuera del cerebro, se añadió la métrica coverage para cuantificar la proporción anatómicamente válida de las activaciones (cantidad de activaciones dentro del cerebro, en referencia a la cantidad de activaciones totales). 
A su vez, se creó un escenario comparativo complementario a los cinco que desarrolló el autor original, siendo el escenario CPH Female BL vs W1W7, realizando una evaluación de la exactitud de predicción, con 10 y 50 épocas.
#--------------------------

Estado del proyecto:
Después de realizar la comparativa mencionada entre los métodos de interpretabilidad, se obtuvo un mejor desempeño para el caso de Grad-CAM++. Aunque Grad-CAM y HiResCAM exhiben las coberturas más altas, presentan variabilidad notable entre sujetos (ratas macho y hembra), posicionando a Grad-CAM++ como el método más estable para el tipo de dato alimentado y el modelo con el que se trabajó. Se sugiere complementar la evaluación efectuada, mediante la incorporación de distintas métricas que permitan abarcar de manera más integral los aspectos que intervienen en la efectividad de los métodos de interpretabilidad.

*A continuación se aborda a detalle, las consideraciones que se deben de tener para poder replicar el presente trabajo, con el objetivo de robustecer el avance efectuado.
#--------------------------

Requisitos de la configuración inicial:
1.- Considerando que la compatibilidad entre versiones de las librerías constituye un aspecto enredoso,  se adjunta el environment, llamado gpuenv_new.yml listo para su configuración: Desde la terminal de Anaconda Prompt ir a la carpeta donde se encuentra la descarga (ponerla dentro de la carpeta donde están todos los códigos de trabajo), y pegar lo siguiente 
conda env create -f gpuenv_new.yml
2.- Considerando que la longitud de las rutas resultó ser una limitante al momento de la carga de datos y el guardado de archivos (las rutas no se reconocían por su extensa longitud), se crearon unidades virtuales para atender a esta problemática. A continuación se presentan las tres unidades virtuales creadas:
Se encuentra inicializado en My_Data_Generator
Para la carga de datos: subst R: "C:\Users\L03117947\Instituto Tecnologico y de Estudios Superiores de Monterrey\Luis Guillermo Hernández Rojas - rabies" 
*Previo a "preprocess_batch-..."
Para el guardado de archivos (se encuentran inicializadas en el código base)
subst W: "C:\Users\L03117947\Downloads\Kerensa\Tesis Alan\Tesis Alan\Neuroimaging-Based-Pain-Detector-Using-Artificial-Intelligence-Approaches-main\Neuroimaging-Based-Pain-Detector-Using-Artificial-Intelligence-Approaches-main" 
subst E: "C:\Users\L03117947\Downloads\Kerensa\Tesis Alan\Tesis Alan\Neuroimaging-Based-Pain-Detector-Using-Artificial-Intelligence-Approaches-main\Neuroimaging-Based-Pain-Detector-Using-Artificial-Intelligence-Approaches-main\GradCamRegistros"
3.- En los códigos de carga de datos (my_data_generator), se deberá modificar toda línea que establezcan el usuario, ajustándolo al correspondiente de cada computadora (ejemplo: os.getlogin() == "NOMBRE DE USUARIO")
4.- En los códigos base, para la variable rootpath1 y mask_nii, se deberá colocar la ruta correspondiente de los archivos base proporcionados (atlas del cerebro)
#--------------------------

Guía de códigos:
En la sección de archivos de GitHub, se encuentran los siguientes siete códigos:
1.- HiResCAM.ipynb: Aplicación del método de interpretabilidad HiResCAM sobre el escenario comparativo de male vs female en la sesión 3 
2.- Respond-CAM.ipynb: Aplicación del método de interpretabilidad Respond-CAM sobre el escenario comparativo de male vs female en la sesión 3 
3.- GradCAM.ipynb: Aplicación del método de interpretabilidad Grad-CAM sobre el escenario comparativo de male vs female en la sesión 3 
4.- GradCAM++.ipynb: Aplicación del método de interpretabilidad Grad-CAM++ sobre el escenario comparativo de male vs female en la sesión 3 
5.- My_Data_Generator: Código para la carga de datos
6.- BLvsW1W7: Comparativa adicional del escenario de CPH Female BL vs W1W7
7.- my_data_generator1: Código para la carga de datos, considerando el escenario complementario BL vs W1W7
#--------------------------


