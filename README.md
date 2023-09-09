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
	
 	Se abrirá una consola en la parte inferior de la pantalla. Una vez caragada, si es primera vez que se abre, mostrará un mensaje preguntando si deseamos leer más sobre *Cloud Shell*
	En el caso de no desear hacerlo, teclear letra N y enter
	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/5398d347-7e6a-40d8-b323-3f5012fa9829)

 
5. Clonar repositorio git desde consola mediante el comando
	```
	git clone https://github.com/whiplash0104/Race2CloudFY24.git
 	```
 	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/1aac26c5-52e1-4020-b0ce-eb34368a450d)
	
 	Este, descargará el contenido necesario para configurar el cluster

6. Una vez desargado entrar al directorio ***Race2CloudFY24*** y ejecutar el script ***configuracionesOKE.sh*** mediante los comandos 
	```
	cd Race2CloudFY24
 	bash configuracionesOKE.sh 
 	```
 	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/d83e682c-d92e-4151-9700-9a89d89aed1a)

	La ejecución de este comando tardará aproximadamente un minuto y al finalizar entregará los datos de acceso a ArgoCD
	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/8788492d-f3a7-4a2d-9567-b8db7fb51f4b)

7. Acceder a la URL entregada por el comando anterior utilizando las credenciales también entregadas (para cada caso las credenciales e ip son distintas)
 	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/5fc8f180-3521-4feb-be63-9aad5adf1513)

8. Una vez dentro de la plataforma debemos crear 3 aplicaciones distintas de la sigueinte forma
	Hacer click en botín ***+ NEW APP***
	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/06adb6f9-1d48-4def-bc47-2e320af0d7e1)

 	Una ve dentro de ***NEW APPLICATION*** a crear la primera definir los siguientes parámetros dentro del apartado ***GENERAL***
 	```
	Application Name:			api-reader
  	Project Name: 				Seleccionar el proyecto default
  	SYYNC POLICY:				Seleccionar la opción Automatic
	Dar click y selecionar en la opción AUTO-CREATE NAMESPACE
  	```
  	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/84f7596b-e74e-4c8a-9059-f5a4dd573438)

	Dentro del apartado SOURCE definir
	```
	Repository URL:				https://github.com/whiplash0104/Race2CloudFY24.git
 	Revision:				main
 	Path:					api-reader/api-reader-manifest
 	```
 	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/29d6535c-4941-43ac-8323-4bbf784c2799)


	Desde el apartado ***DESTINATION***
	```
	Cluster URL:				Seleccionar la opción https://kubernetes.default.svc
 	Namespace:				api-reader
 	```
 	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/cf41c3f9-24c4-431a-ac57-0697c73bfafb)

	Finalmente dar click en el botón ***CREATE***
	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/3d466c5a-9e11-4100-b67a-9f194cc337fd)

	Posterior a ello, ArgoCD comenzará a deslegar la aplicación en el cluster.

	Se verá de color celeste mientras desplega
	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/5bf4aa77-677c-434b-9a4c-47802205042d)

	Si el proceso de despliegue finalizó de forma correcta cambiará a color verde
	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/36c2fe79-7f47-40bb-9bba-9da04c8c2c5f)

 
10. Repetir el mismo proceso para las próximas dos aplicaciones
	Click en ***NEW APPLICATION*** y definir los siguientes parámetros
 	```
	Application Name:			oci-reader
  	Project Name: 				Seleccionar el proyecto default
  	SYYNC POLICY:				Seleccionar la opción Automatic
	Dar click y selecionar en la opción AUTO-CREATE NAMESPACE
  	Repository URL:				https://github.com/whiplash0104/Race2CloudFY24.git
 	Revision:				main
 	Path:					oci-reader/oci-reader-manifest
  	Cluster URL:				Seleccionar la opción https://kubernetes.default.svc
 	Namespace:				oci-reader
  	```
	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/09740c03-d10a-4b16-9b03-36b0b1631c37)
	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/e92bb58f-c2be-44a3-a825-f924fcfe7a9b)

	Podemos notar que mientras se despliega la nueva aplicación tenemos un porcentaje en verde y otro en celeste
	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/f84b23c2-6d3d-4a59-9914-81984d54ed1d)

	Una vez finalizado el despliegue de forma correcta podemos ver todo en verde
	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/988635cb-48da-463e-b5a3-a603afe8d300)


12. a
13. a
14. a
15. a
16. a
17. a
18. a
19. 
