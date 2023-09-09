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
	Menu > Identity & Security > Compartmente > New Compartment
	```
	CAMPO				VALOR
	==============================================
	Name		 		OKE
	Description 			OKE
	Parent Compartment 		XXXXX (root)

1. Crear Cluster 

### Actividades post creación cluster

1. Posterior a la creación del cluster OKE, acceder a este
	Menu > Developer Services > Kubernetes Clusters (OKE)
	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/af8781b0-f2fa-4575-97ff-a6705f171d20)

2. Acceder a cluster creado (el nombre del cluster puede variar)
	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/f3bb88c2-7c30-43cc-8726-027f68b2d993)
	

3. Hacer click en "Access Cluster" 
	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/8e77f63a-87d9-421c-a27d-f2f765c8e21f)

   	Dejar seleccionada la opción "Cloud Shell Access" y hacer click en el botón "Launch Cloud shell"
   	![image](https://github.com/whiplash0104/Race2CloudFY24/assets/14284928/acb9614c-a301-4600-abd8-5efbea27653b)

4. 
