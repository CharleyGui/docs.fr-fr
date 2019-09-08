---
title: 'Procédure : créer un gestionnaire d’autorisations personnalisé pour un service'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Communication Foundation, extending
- OperationRequirement class
ms.assetid: 6214afde-44c1-4bf5-ba07-5ad6493620ea
ms.openlocfilehash: 9c28cb81b78f80505cfcf5f7e4dfdba083bd0793
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797108"
---
# <a name="how-to-create-a-custom-authorization-manager-for-a-service"></a><span data-ttu-id="53725-102">Procédure : créer un gestionnaire d’autorisations personnalisé pour un service</span><span class="sxs-lookup"><span data-stu-id="53725-102">How to: Create a Custom Authorization Manager for a Service</span></span>

<span data-ttu-id="53725-103">L’infrastructure de modèle d’identité dans Windows Communication Foundation (WCF) prend en charge un modèle d’autorisation extensible basé sur les revendications.</span><span class="sxs-lookup"><span data-stu-id="53725-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) supports an extensible claims-based authorization model.</span></span> <span data-ttu-id="53725-104">Les revendications sont extraites de jetons et sont éventuellement traitées par les stratégies d'autorisation personnalisées puis placées dans un <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="53725-104">Claims are extracted from tokens and optionally processed by custom authorization policies and then placed into an <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span> <span data-ttu-id="53725-105">Un gestionnaire d'autorisations examine les revendications dans le <xref:System.IdentityModel.Policy.AuthorizationContext> pour prendre des décisions concernant les autorisations.</span><span class="sxs-lookup"><span data-stu-id="53725-105">An authorization manager examines the claims in the <xref:System.IdentityModel.Policy.AuthorizationContext> to make authorization decisions.</span></span>

<span data-ttu-id="53725-106">Par défaut, les décisions relatives aux autorisations sont prises par la classe <xref:System.ServiceModel.ServiceAuthorizationManager> ; cependant, ces décisions peuvent être substituées en créant un gestionnaire d'autorisations personnalisé.</span><span class="sxs-lookup"><span data-stu-id="53725-106">By default, authorization decisions are made by the <xref:System.ServiceModel.ServiceAuthorizationManager> class; however these decisions can be overridden by creating a custom authorization manager.</span></span> <span data-ttu-id="53725-107">Pour créer un gestionnaire d'autorisations personnalisé, créez une classe qui dérive de <xref:System.ServiceModel.ServiceAuthorizationManager> et implémente la méthode <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>.</span><span class="sxs-lookup"><span data-stu-id="53725-107">To create a custom authorization manager, create a class that derives from <xref:System.ServiceModel.ServiceAuthorizationManager> and implement <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="53725-108">Les décisions relatives aux autorisations sont prises dans la méthode <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>, qui retourne la valeur `true` lorsque l'accès est accordé et `false` lorsque l'accès est refusé.</span><span class="sxs-lookup"><span data-stu-id="53725-108">Authorization decisions are made in the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method, which returns `true` when access is granted and `false` when access is denied.</span></span>

<span data-ttu-id="53725-109">Si la décision d'autorisation dépend du contenu du corps de message, utilisez la méthode <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A>.</span><span class="sxs-lookup"><span data-stu-id="53725-109">If the authorization decision depends on the contents of the message body, use the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method.</span></span>

<span data-ttu-id="53725-110">En raison des problèmes de performances, essayez de reconcevoir si possible votre application afin que la décision d'autorisation ne nécessite pas l'accès au corps du message.</span><span class="sxs-lookup"><span data-stu-id="53725-110">Because of performance issues, if possible you should redesign your application so that the authorization decision does not require access to the message body.</span></span>

<span data-ttu-id="53725-111">L'enregistrement du gestionnaire d'autorisations personnalisé pour un service peut être réalisé dans du code ou dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="53725-111">Registration of the custom authorization manager for a service can be done in code or configuration.</span></span>

### <a name="to-create-a-custom-authorization-manager"></a><span data-ttu-id="53725-112">Pour créer un gestionnaire d'autorisations personnalisé</span><span class="sxs-lookup"><span data-stu-id="53725-112">To create a custom authorization manager</span></span>

1. <span data-ttu-id="53725-113">Dérivez une classe d'une classe de la classe <xref:System.ServiceModel.ServiceAuthorizationManager>.</span><span class="sxs-lookup"><span data-stu-id="53725-113">Derive a class from the <xref:System.ServiceModel.ServiceAuthorizationManager> class.</span></span>

    [!code-csharp[c_CustomAuthMgr#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#5)]
    [!code-vb[c_CustomAuthMgr#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#5)]

2. <span data-ttu-id="53725-114">Remplacez la méthode <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> .</span><span class="sxs-lookup"><span data-stu-id="53725-114">Override the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> method.</span></span>

    <span data-ttu-id="53725-115">Utilisez le <xref:System.ServiceModel.OperationContext> passé à la méthode <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> pour prendre des décisions concernant les autorisations.</span><span class="sxs-lookup"><span data-stu-id="53725-115">Use the <xref:System.ServiceModel.OperationContext> that is passed to the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> method to make authorization decisions.</span></span>

    <span data-ttu-id="53725-116">L'exemple de code suivant utilise la méthode <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> pour rechercher la revendication personnalisée `http://www.contoso.com/claims/allowedoperation` afin de prendre une décision relative à une autorisation.</span><span class="sxs-lookup"><span data-stu-id="53725-116">The following code example uses the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> method to find the custom claim `http://www.contoso.com/claims/allowedoperation` to make an authorization decision.</span></span>

    [!code-csharp[c_CustomAuthMgr#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#6)]
    [!code-vb[c_CustomAuthMgr#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#6)]

### <a name="to-register-a-custom-authorization-manager-using-code"></a><span data-ttu-id="53725-117">Pour enregistrer un gestionnaire d'autorisations personnalisé à l'aide de code</span><span class="sxs-lookup"><span data-stu-id="53725-117">To register a custom authorization manager using code</span></span>

1. <span data-ttu-id="53725-118">Créez une instance du gestionnaire d'autorisations personnalisé et assignez-la à la propriété <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A>.</span><span class="sxs-lookup"><span data-stu-id="53725-118">Create an instance of the custom authorization manager and assign it to the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> property.</span></span>

    <span data-ttu-id="53725-119"><xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> est accessible à l'aide de la propriété <xref:System.ServiceModel.ServiceHostBase.Authorization%2A>.</span><span class="sxs-lookup"><span data-stu-id="53725-119">The <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> can be accessed using <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> property.</span></span>

    <span data-ttu-id="53725-120">L'exemple de code suivant enregistre le gestionnaire d'autorisations personnalisé `MyServiceAuthorizationManager`.</span><span class="sxs-lookup"><span data-stu-id="53725-120">The following code example registers the `MyServiceAuthorizationManager` custom authorization manager.</span></span>

    [!code-csharp[c_CustomAuthMgr#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#4)]
    [!code-vb[c_CustomAuthMgr#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#4)]

### <a name="to-register-a-custom-authorization-manager-using-configuration"></a><span data-ttu-id="53725-121">Pour enregistrer un gestionnaire d'autorisations personnalisé à l'aide d'une configuration</span><span class="sxs-lookup"><span data-stu-id="53725-121">To register a custom authorization manager using configuration</span></span>

1. <span data-ttu-id="53725-122">Ouvrez le fichier de configuration pour le service.</span><span class="sxs-lookup"><span data-stu-id="53725-122">Open the configuration file for the service.</span></span>

2. <span data-ttu-id="53725-123">Ajoutez un [ \<](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) [ >ServiceAuthorizationau>decomportements.\<](../../configure-apps/file-schema/wcf/behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="53725-123">Add a [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to the [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md).</span></span>

    <span data-ttu-id="53725-124">Pour le [ \<> ServiceAuthorization](../../configure-apps/file-schema/wcf/serviceauthorization-element.md), ajoutez un `serviceAuthorizationManagerType` attribut et définissez sa valeur sur le type qui représente le gestionnaire d’autorisations personnalisé.</span><span class="sxs-lookup"><span data-stu-id="53725-124">To the [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md), add a `serviceAuthorizationManagerType` attribute and set its value to the type that represents the custom authorization manager.</span></span>

3. <span data-ttu-id="53725-125">Ajoutez une liaison qui sécurise la communication entre le client et le service.</span><span class="sxs-lookup"><span data-stu-id="53725-125">Add a binding that secures the communication between the client and service.</span></span>

    <span data-ttu-id="53725-126">La liaison choisie pour cette communication détermine les revendications ajoutées au <xref:System.IdentityModel.Policy.AuthorizationContext>, que le gestionnaire d'autorisations personnalisé utilise pour prendre des décisions concernant les autorisations.</span><span class="sxs-lookup"><span data-stu-id="53725-126">The binding that is chosen for this communication determines the claims that are added to the <xref:System.IdentityModel.Policy.AuthorizationContext>, which the custom authorization manager uses to make authorization decisions.</span></span> <span data-ttu-id="53725-127">Pour plus d’informations sur les liaisons fournies par le système, consultez [liaisons fournies par le système](../system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="53725-127">For more details about the system-provided bindings, see [System-Provided Bindings](../system-provided-bindings.md).</span></span>

4. <span data-ttu-id="53725-128">Associez le comportement à un point de terminaison de service [ \<](../../configure-apps/file-schema/wcf/service.md) , en ajoutant un élément de > de service `behaviorConfiguration` et en définissant la valeur de l’attribut sur la valeur de l’attribut Name pour l' [ \<élément Behavior >](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="53725-128">Associate the behavior to a service endpoint, by adding a [\<service>](../../configure-apps/file-schema/wcf/service.md) element and set the value of the `behaviorConfiguration` attribute to the value of the name attribute for the [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>

    <span data-ttu-id="53725-129">Pour plus d’informations sur la configuration d’un point de [terminaison de service, consultez Procédure : Créez un point de terminaison de](../feature-details/how-to-create-a-service-endpoint-in-configuration.md)service dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="53725-129">For more information about configuring a service endpoint, see [How to: Create a Service Endpoint in Configuration](../feature-details/how-to-create-a-service-endpoint-in-configuration.md).</span></span>

    <span data-ttu-id="53725-130">L'exemple de code suivant enregistre le gestionnaire d'autorisations personnalisé `Samples.MyServiceAuthorizationManager`.</span><span class="sxs-lookup"><span data-stu-id="53725-130">The following code example registers the custom authorization manager `Samples.MyServiceAuthorizationManager`.</span></span>

    ```xml
    <configuration>
      <system.serviceModel>
        <services>
          <service
              name="Microsoft.ServiceModel.Samples.CalculatorService"
              behaviorConfiguration="CalculatorServiceBehavior">
            <host>
              <baseAddresses>
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
              </baseAddresses>
            </host>
            <endpoint address=""
                      binding="wsHttpBinding_Calculator"
                      contract="Microsoft.ServiceModel.Samples.ICalculator" />
          </service>
        </services>
        <bindings>
          <WSHttpBinding>
           <binding name = "wsHttpBinding_Calculator">
             <security mode="Message">
               <message clientCredentialType="Windows"/>
             </security>
            </binding>
          </WSHttpBinding>
        </bindings>
        <behaviors>
          <serviceBehaviors>
            <behavior name="CalculatorServiceBehavior">
              <serviceAuthorization serviceAuthorizationManagerType="Samples.MyServiceAuthorizationManager,MyAssembly" />
             </behavior>
         </serviceBehaviors>
       </behaviors>
      </system.serviceModel>
    </configuration>
    ```

    > [!WARNING]
    > <span data-ttu-id="53725-131">Notez que lorsque vous spécifiez serviceAuthorizationManagerType, la chaîne doit contenir le nom de type qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="53725-131">Note that when you specify the serviceAuthorizationManagerType, the string must contain the fully qualified type name.</span></span> <span data-ttu-id="53725-132">une virgule, et le nom de l'assembly dans lequel le type est défini.</span><span class="sxs-lookup"><span data-stu-id="53725-132">a comma, and the name of the assembly in which the type is defined.</span></span> <span data-ttu-id="53725-133">Si vous omettez le nom de l'assembly, WCF tentera de charger le type à partir de System.ServiceModel.dll.</span><span class="sxs-lookup"><span data-stu-id="53725-133">If you leave out the assembly name, WCF will attempt to load the type from System.ServiceModel.dll.</span></span>

## <a name="example"></a><span data-ttu-id="53725-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="53725-134">Example</span></span>

<span data-ttu-id="53725-135">L'exemple de code suivant illustre une implémentation de base d'une classe <xref:System.ServiceModel.ServiceAuthorizationManager> qui inclut la substitution de la méthode <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>.</span><span class="sxs-lookup"><span data-stu-id="53725-135">The following code example demonstrates a basic implementation of a <xref:System.ServiceModel.ServiceAuthorizationManager> class that includes overriding the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="53725-136">L'exemple de code recherche une revendication personnalisée dans le <xref:System.IdentityModel.Policy.AuthorizationContext> et retourne la valeur `true` lorsque la ressource pour cette revendication personnalisée correspond à la valeur d'action du <xref:System.ServiceModel.OperationContext>.</span><span class="sxs-lookup"><span data-stu-id="53725-136">The example code examines the <xref:System.IdentityModel.Policy.AuthorizationContext> for a custom claim and returns `true` when the resource for that custom claim matches the action value from the <xref:System.ServiceModel.OperationContext>.</span></span> <span data-ttu-id="53725-137">Pour une implémentation plus complète d’une <xref:System.ServiceModel.ServiceAuthorizationManager> classe, consultez [stratégie d’autorisation](../samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="53725-137">For a more complete implementation of a <xref:System.ServiceModel.ServiceAuthorizationManager> class, see [Authorization Policy](../samples/authorization-policy.md).</span></span>

[!code-csharp[c_CustomAuthMgr#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#2)]
[!code-vb[c_CustomAuthMgr#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#2)]

## <a name="see-also"></a><span data-ttu-id="53725-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53725-138">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="53725-139">Stratégie d’autorisation</span><span class="sxs-lookup"><span data-stu-id="53725-139">Authorization Policy</span></span>](../samples/authorization-policy.md)
