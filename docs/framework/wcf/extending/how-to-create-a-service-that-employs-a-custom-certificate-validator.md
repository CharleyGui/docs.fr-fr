---
title: 'Comment : créer un service qui utilise un validateur de certificat personnalisé'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
ms.openlocfilehash: af1bb9b2ff793f6e6854c1b253dd445a35a5076f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185577"
---
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a><span data-ttu-id="a2d2f-102">Comment : créer un service qui utilise un validateur de certificat personnalisé</span><span class="sxs-lookup"><span data-stu-id="a2d2f-102">How to: Create a Service that Employs a Custom Certificate Validator</span></span>
<span data-ttu-id="a2d2f-103">Cette rubrique décrit comment implémenter un validateur de certificat personnalisé et comment configurer les informations d’identification du service ou du client pour remplacer la logique de validation de certificat par défaut par le validateur de certificat personnalisé.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-103">This topic shows how to implement a custom certificate validator and how to configure client or service credentials to replace the default certificate validation logic with the custom certificate validator.</span></span>  
  
 <span data-ttu-id="a2d2f-104">Si le certificat X.509 est utilisé pour authentifier un client ou un service, Windows Communication Foundation (WCF) utilise par défaut le magasin de certificats Windows et l’API Crypto pour valider le certificat et s’assurer qu’il est fiable.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-104">If the X.509 certificate is used to authenticate a client or service, Windows Communication Foundation (WCF) by default uses the Windows certificate store and Crypto API to validate the certificate and to ensure that it is trusted.</span></span> <span data-ttu-id="a2d2f-105">Les fonctionnalités intégrées de validation du certificat sont parfois insuffisantes et doivent être changées.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-105">Sometimes the built-in certificate validation functionality is not enough and must be changed.</span></span> <span data-ttu-id="a2d2f-106">WCF offre un moyen facile de modifier la logique de validation en permettant aux utilisateurs d’ajouter un validateur de certificat personnalisé.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-106">WCF provides an easy way to change the validation logic by allowing users to add a custom certificate validator.</span></span> <span data-ttu-id="a2d2f-107">Si un validateur de certificat personnalisé est spécifié, WCF n’utilise pas la logique intégrée de validation des certificats, mais s’appuie plutôt sur le validateur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-107">If a custom certificate validator is specified, WCF does not use the built-in certificate validation logic but relies on the custom validator instead.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="a2d2f-108">Procédures</span><span class="sxs-lookup"><span data-stu-id="a2d2f-108">Procedures</span></span>  
  
#### <a name="to-create-a-custom-certificate-validator"></a><span data-ttu-id="a2d2f-109">Pour créer un validateur de certificat personnalisé</span><span class="sxs-lookup"><span data-stu-id="a2d2f-109">To create a custom certificate validator</span></span>  
  
1. <span data-ttu-id="a2d2f-110">Définissez une nouvelle classe dérivée de <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-110">Define a new class derived from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span>  
  
2. <span data-ttu-id="a2d2f-111">Implémentez la méthode abstraite <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-111">Implement the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> method.</span></span> <span data-ttu-id="a2d2f-112">Le certificat qui doit être validé est passé sous la forme d’un argument à la méthode.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-112">The certificate that must be validated is passed as an argument to the method.</span></span> <span data-ttu-id="a2d2f-113">Si le certificat passé n’est pas valide selon la logique de validation, cette méthode lève une <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-113">If the passed certificate is not valid according to the validation logic, this method throws a <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>.</span></span> <span data-ttu-id="a2d2f-114">Si le certificat est valide, la méthode est retournée à l'appelant.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-114">If the certificate is valid, the method returns to the caller.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a2d2f-115">Pour renvoyer des erreurs d'authentification au client, levez une exception <xref:System.ServiceModel.FaultException> dans la méthode <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-115">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a><span data-ttu-id="a2d2f-116">Pour spécifier un validateur de certificat personnalisé dans la configuration du service</span><span class="sxs-lookup"><span data-stu-id="a2d2f-116">To specify a custom certificate validator in service configuration</span></span>  
  
1. <span data-ttu-id="a2d2f-117">Ajoutez [ \<](../../configure-apps/file-schema/wcf/behaviors.md) un comportement>élément et un [ \<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) à l’élément [ \<>system.serviceModel.](../../configure-apps/file-schema/wcf/system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a2d2f-117">Add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element and a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="a2d2f-118">Ajoutez [ \<](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) un comportement>et `name` définissez l’attribut à une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-118">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>  
  
3. <span data-ttu-id="a2d2f-119">Ajoutez un [ \<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) à `<behavior>` l’élément.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-119">Add a [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) to the `<behavior>` element.</span></span>  
  
4. <span data-ttu-id="a2d2f-120">Ajoutez un élément `<clientCertificate>` à l'élément `<serviceCredentials>`.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-120">Add a `<clientCertificate>` element to the `<serviceCredentials>` element.</span></span>  
  
5. <span data-ttu-id="a2d2f-121">Ajoutez une [ \<authentification](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) `<clientCertificate>`>à l’élément.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-121">Add an [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) to the `<clientCertificate>` element.</span></span>  
  
6. <span data-ttu-id="a2d2f-122">Affectez à l'attribut `customCertificateValidatorType` le type de validateur.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-122">Set the `customCertificateValidatorType` attribute to the validator type.</span></span> <span data-ttu-id="a2d2f-123">L'exemple suivant affecte à l'attribut l'espace de noms et le nom du type.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-123">The following example sets the attribute to the namespace and name of the type.</span></span>  
  
7. <span data-ttu-id="a2d2f-124">Affectez à l'attribut `certificateValidationMode` la valeur `Custom`.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-124">Set the `certificateValidationMode` attribute to `Custom`.</span></span>  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
       <serviceBehaviors>  
        <behavior name="ServiceBehavior">  
         <serviceCredentials>  
          <clientCertificate>  
          <authentication certificateValidationMode="Custom" customCertificateValidatorType="Samples.MyValidator, service" />  
          </clientCertificate>  
         </serviceCredentials>  
        </behavior>  
       </serviceBehaviors>  
      </behaviors>  
    </system.serviceModel>  
    </configuration>  
    ```  
  
#### <a name="to-specify-a-custom-certificate-validator-using-configuration-on-the-client"></a><span data-ttu-id="a2d2f-125">Pour spécifier un validateur de certificat personnalisé à l'aide de la configuration sur le client</span><span class="sxs-lookup"><span data-stu-id="a2d2f-125">To specify a custom certificate validator using configuration on the client</span></span>  
  
1. <span data-ttu-id="a2d2f-126">Ajoutez [ \<](../../configure-apps/file-schema/wcf/behaviors.md) un comportement>élément et un [ \<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) à l’élément [ \<>system.serviceModel.](../../configure-apps/file-schema/wcf/system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a2d2f-126">Add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element and a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="a2d2f-127">Ajouter un [ \<point finalBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) élément.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-127">Add an [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) element.</span></span>  
  
3. <span data-ttu-id="a2d2f-128">Ajoutez un élément `<behavior>`, puis affectez à l'attribut `name` une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-128">Add a `<behavior>` element and set the `name` attribute to an appropriate value.</span></span>  
  
4. <span data-ttu-id="a2d2f-129">Ajouter un [ \<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) élément.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-129">Add a [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>  
  
5. <span data-ttu-id="a2d2f-130">Ajouter un [ \<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="a2d2f-130">Add a [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).</span></span>  
  
6. <span data-ttu-id="a2d2f-131">Ajoutez une [ \<>d’authentification](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) comme indiqué sur l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-131">Add an [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) as shown on the following example.</span></span>  
  
7. <span data-ttu-id="a2d2f-132">Affectez à l'attribut `customCertificateValidatorType` le type de validateur.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-132">Set the `customCertificateValidatorType` attribute to the validator type.</span></span>  
  
8. <span data-ttu-id="a2d2f-133">Affectez à l'attribut `certificateValidationMode` la valeur `Custom`.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-133">Set the `certificateValidationMode` attribute to `Custom`.</span></span> <span data-ttu-id="a2d2f-134">L'exemple suivant affecte à l'attribut l'espace de noms et le nom du type.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-134">The following example sets the attribute to the namespace and name of the type.</span></span>  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
       <endpointBehaviors>  
        <behavior name="clientBehavior">  
         <clientCredentials>  
          <serviceCertificate>  
           <authentication certificateValidationMode="Custom"
                  customCertificateValidatorType=  
             "Samples.CustomX509CertificateValidator, client"/>  
          </serviceCertificate>  
         </clientCredentials>  
        </behavior>  
       </endpointBehaviors>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-service"></a><span data-ttu-id="a2d2f-135">Pour spécifier un validateur de certificat personnalisé à l'aide du code sur le service</span><span class="sxs-lookup"><span data-stu-id="a2d2f-135">To specify a custom certificate validator using code on the service</span></span>  
  
1. <span data-ttu-id="a2d2f-136">Spécifiez le validateur de certificat personnalisé sur la propriété <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-136">Specify the custom certificate validator on the <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> property.</span></span> <span data-ttu-id="a2d2f-137">Vous pouvez accéder aux informations d'identification de service à l'aide de la propriété <xref:System.ServiceModel.ServiceHostBase.Credentials%2A>.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-137">You can access the service credentials using the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property.</span></span>  
  
2. <span data-ttu-id="a2d2f-138">Attribuez à la propriété <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> la valeur <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-138">Set the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> property to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span></span>  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a><span data-ttu-id="a2d2f-139">Pour spécifier un validateur de certificat personnalisé à l'aide du code sur le client</span><span class="sxs-lookup"><span data-stu-id="a2d2f-139">To specify a custom certificate validator using code on the client</span></span>  
  
1. <span data-ttu-id="a2d2f-140">Spécifiez le validateur de certificat personnalisé à l'aide de la propriété <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A>.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-140">Specify the custom certificate validator using the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> property.</span></span> <span data-ttu-id="a2d2f-141">Vous pouvez accéder aux informations d'identification du client à l'aide de la propriété <xref:System.ServiceModel.ServiceHostBase.Credentials%2A>.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-141">You can access the client credentials using the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property.</span></span> <span data-ttu-id="a2d2f-142">(La classe client générée par [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) dérive toujours de la <xref:System.ServiceModel.ClientBase%601> classe.)</span><span class="sxs-lookup"><span data-stu-id="a2d2f-142">(The client class generated by [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) always derives from the <xref:System.ServiceModel.ClientBase%601> class.)</span></span>  
  
2. <span data-ttu-id="a2d2f-143">Attribuez à la propriété <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> la valeur <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-143">Set the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> property to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2d2f-144"> Exemple</span><span class="sxs-lookup"><span data-stu-id="a2d2f-144">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="a2d2f-145">Description</span><span class="sxs-lookup"><span data-stu-id="a2d2f-145">Description</span></span>  
 <span data-ttu-id="a2d2f-146">L'exemple suivant montre une implémentation d'un validateur de certificat personnalisé et son utilisation sur le service.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-146">The following sample shows an implementation of a custom certificate validator and its usage on the service.</span></span>  
  
### <a name="code"></a><span data-ttu-id="a2d2f-147">Code</span><span class="sxs-lookup"><span data-stu-id="a2d2f-147">Code</span></span>  
 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a2d2f-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2d2f-148">See also</span></span>

- <xref:System.IdentityModel.Selectors.X509CertificateValidator>
