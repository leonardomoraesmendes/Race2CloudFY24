## CD Automatizado Mediante ArgoCD en Cluster OKE

## ##

### Requerimientos:

- Cuenta de Oracle Cloud Infrastructure(test gratuito https://www.oracle.com/cloud/free/)
- Cuenta de Github (https://github.com/signup?ref_cta=Sign+up&ref_loc=header+logged+out&ref_page=%2F&source=header-home)

### ¿Qué vamos a hacer?

- Clonar repositorio GitHub
- Configurar OKE
- Desplegar aplicación mediante ArgoCD

### Paso a Paso

0. Crear Compartment
	```
 	Menu > Identity & Security > Compartmente > New Compartment
	```
	CAMPO				VALOR
	==============================================
	Name		 		OKE
	Description 			OKE
	Parent Compartment 		XXXXX (root)
	```
 
1. Crear Cluster 

### Actividades post creación cluster

1. Posterior a la creación del cluster OKE, acceder a este
	Menu > Developer Services > Kubernetes Clusters (OKE)
	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/af8781b0-f2fa-4575-97ff-a6705f171d20)

2. Acceder a cluster creado (el nombre del cluster puede variar)
	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/f3bb88c2-7c30-43cc-8726-027f68b2d993)
	

3. Hacer click en **"Access Cluster"** 
	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/8e77f63a-87d9-421c-a27d-f2f765c8e21f)

   	Dejar seleccionada la opción "Cloud Shell Access" y hacer click en el botón "Launch Cloud shell"
   	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/acb9614c-a301-4600-abd8-5efbea27653b)
	
 	Se abrirá una consola en la parte inferior de la pantalla. Una vez caragada, 
 
4. Clonar repositorio git desde consola mediante el comando
	```
	git clone https://github.com/whiplash0104/Race2CloudFY24.git
 	```
 	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/1aac26c5-52e1-4020-b0ce-eb34368a450d)
	
 	Este, descargará el contenido necesario para configurar el cluster

5. Una vez desargado entrar al directorio ***"Race2CloudFY24"*** y ejecutar el script ***configuracionesOKE.sh*** mediante los comandos 
	```
	cd Race2CloudFY24
 	bash configuracionesOKE.sh 
 	```
 	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/d83e682c-d92e-4151-9700-9a89d89aed1a)

	La ejecución de este comando tardará aproximadamente un minuto y al finalizar entregará los datos de acceso a ArgoCD
	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/8788492d-f3a7-4a2d-9567-b8db7fb51f4b)


6. das
7. das
8. da
9. a
10. a
11. 
