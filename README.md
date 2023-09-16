## CD Automatizado Mediante ArgoCD en Cluster OKE

## ##

### Requerimientos:

- Cuenta de Oracle Cloud Infrastructure(test gratuito https://www.oracle.com/cloud/free/)

### ¿Qué vamos a hacer?

- Clonar repositorio GitHub
- Configurar OKE
- Desplegar aplicación mediante ArgoCD

### Paso a Paso

### Actividades post creación cluster

1. Posterior a la creación del cluster OKE, acceder a este
	Menu > Developer Services > Kubernetes Clusters (OKE)
	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/af8781b0-f2fa-4575-97ff-a6705f171d20)

3. Acceder a cluster creado (el nombre del cluster puede variar)
   
	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/40583067/56f2949d-43c4-4999-a91e-6732affc4d22)

4. Hacer click en la parte superior para abrir la consola del **"Cloud Shell"**

	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/40583067/c281f159-c86e-4051-b12f-618c447739ab)

	Se abrirá una consola en la parte inferior de la pantalla. Una vez caragada, si es primera vez que se abre, mostrará un mensaje 	preguntando si deseamos leer más sobre *Cloud Shell*
	En el caso de no desear hacerlo, teclear letra N y enter

5. Como el Cluster de Kubernetes esta configurado en una **"subred privada"** debemos crear un acceso privado

	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/40583067/2fa17022-c6b8-416f-b8df-3fc7679b91cc)

	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/40583067/d2ca2f22-0edd-4b32-a77c-6b3caa277757)
	
	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/40583067/91486d4a-1909-4e30-8acf-057630ea4620)

	

	Posteriormente nuestra consola de Cloud Shell se va conectar por medio de una interface privada en la red del cluster de Kubernetes

 	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/40583067/dc2253d4-00c1-41db-9cf0-017f215a3c94)

7. Ahora hacer click en **"Access Cluster"**

   	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/40583067/a1f39e2c-39fc-4cd0-98b4-5581f3978117)

   
8. Ahora se mostraran los comandos que se deben copiar y pegar para ejecutar en la consola del *Cloud Shell*

	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/40583067/383a892e-228a-4f0f-bbb2-315b740b5bf8)

	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/40583067/05ae701e-d6cd-422c-9f9a-f21abc8aa2ba)

 
9. Clonar repositorio git desde consola mediante el comando
	```
	git clone https://github.com/whiplash0104/Race2CloudFY24.git
 	```
 	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/1aac26c5-52e1-4020-b0ce-eb34368a450d)
	
 	Este, descargará el contenido necesario para configurar el cluster

12. Una vez desargado entrar al directorio ***Race2CloudFY24*** y ejecutar el script ***configuracionesOKE.sh*** mediante los comandos 
	```
	cd Race2CloudFY24
 	bash configuracionesOKE.sh 
 	```
 	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/d83e682c-d92e-4151-9700-9a89d89aed1a)

	La ejecución de este comando tardará aproximadamente un minuto y al finalizar entregará los datos de acceso a ArgoCD
	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/8788492d-f3a7-4a2d-9567-b8db7fb51f4b)

13. Acceder a la URL entregada por el comando anterior utilizando las credenciales también entregadas (para cada caso las credenciales e ip son distintas)
 	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/5fc8f180-3521-4feb-be63-9aad5adf1513)

14. Una vez dentro de la plataforma debemos crear 3 aplicaciones distintas de la siguiente forma
	Hacer click en botón ***+ NEW APP***
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


15. Repetir el mismo proceso para la siguiente aplicación
	Click en ***NEW APPLICATION*** y definir los siguientes parámetros
 	```
	Application Name:			oci-transcribe
  	Project Name: 				Seleccionar el proyecto default
  	SYYNC POLICY:				Seleccionar la opción Automatic
	Dar click y selecionar en la opción AUTO-CREATE NAMESPACE
  	Repository URL:				https://github.com/whiplash0104/Race2CloudFY24.git
 	Revision:				main
 	Path:					oci-transcribe/oci-transcribe-manifest
  	Cluster URL:				Seleccionar la opción https://kubernetes.default.svc
 	Namespace:				oci-transcribe
  	```
  	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/722a700b-5ccf-4587-ab75-ef0f50599335)
	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/b904c0bb-6e34-4312-acb5-5e51e9fdc1de)


	Podemos notar que la nueva aplicación ya esta desplegada
	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/40583067/7bb44188-3313-4133-ad18-e9f38dd056c0)



	Al hacer click en estas podemos ver el detalle de lo desplegado
	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/40583067/3bc6200e-c1d0-42ad-87da-f8ab24e57c80)
 
17. Repetir el mismo proceso para la última aplicación
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

	Podemos notar que la nueva aplicación tenemos un porcentaje en verde y otro en celeste
	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/40583067/da7beb6a-9751-43ba-9464-207aadcf6235)

	Una vez finalizado deberíamos tener las tres aplicaciones ejecutandose de forma correcta
	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/4faa5440-eea7-4a2a-811a-0b87d3af0ece)
	

19. Para conectar a la aplicación desplegada dentro del ***Cloud Shell*** ejecutar
	```
	kubectl get service -n ingress-nginx | grep LoadBalancer | awk '{print $4}'
 	```
 	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/98e7e60c-e995-433d-bc0a-b7ff34e9dcce)

20. Acceder a la IP pública entregada por medio del navegador web.
