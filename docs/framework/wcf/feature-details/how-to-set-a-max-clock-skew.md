---
title: 'Procédure : définir une inclinaison de l’horloge maximale'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MaxClockSkew property
- WCF, custom bindings
ms.assetid: 491d1705-eb29-43c2-a44c-c0cf996f74eb
ms.openlocfilehash: 8dd38f3d07773a4be67648b9c1830206438200d6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242875"
---
# <a name="how-to-set-a-max-clock-skew"></a><span data-ttu-id="d6351-102">Procédure : définir une inclinaison de l’horloge maximale</span><span class="sxs-lookup"><span data-stu-id="d6351-102">How to: Set a Max Clock Skew</span></span>

<span data-ttu-id="d6351-103">Les fonctions à durée critique peuvent dérailler si les paramètres de l'horloge sont différents sur deux ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="d6351-103">Time-critical functions can be derailed if the clock settings on two computers are different.</span></span> <span data-ttu-id="d6351-104">Pour limiter cette possibilité, vous pouvez affecter à la propriété `MaxClockSkew` un <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="d6351-104">To mitigate this possibility, you can set the `MaxClockSkew` property to a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="d6351-105">Cette propriété est disponible sur deux classes :</span><span class="sxs-lookup"><span data-stu-id="d6351-105">This property is available on two classes:</span></span>  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
> <span data-ttu-id="d6351-106">Pour une conversation sécurisée, les modifications apportées à la `MaxClockSkew` propriété doivent être effectuées lorsque le service ou le client est amorcé.</span><span class="sxs-lookup"><span data-stu-id="d6351-106">For a secure conversation, changes to the `MaxClockSkew` property  must be made when the service or client is bootstrapped.</span></span> <span data-ttu-id="d6351-107">Pour ce faire, vous devez définir la propriété sur le <xref:System.ServiceModel.Channels.SecurityBindingElement> retourné par la <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="d6351-107">To do this, you must set the property on the <xref:System.ServiceModel.Channels.SecurityBindingElement> returned by the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="d6351-108">Pour modifier la propriété sur l'une des liaisons fournies par le système, vous devez rechercher l'élément de liaison de sécurité dans la collection de liaisons et affecter une nouvelle valeur à la propriété `MaxClockSkew`.</span><span class="sxs-lookup"><span data-stu-id="d6351-108">To change the property on one of the system-provided bindings, you must find the security binding element in the collection of bindings and set the `MaxClockSkew` property to a new value.</span></span> <span data-ttu-id="d6351-109">Deux classes dérivent de <xref:System.ServiceModel.Channels.SecurityBindingElement> : <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> et <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="d6351-109">Two classes derive from the <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="d6351-110">Lorsque vous récupérez la liaison de sécurité de la collection, vous devez effectuer une conversion de type en l’un de ces types afin de définir correctement la propriété `MaxClockSkew`.</span><span class="sxs-lookup"><span data-stu-id="d6351-110">When retrieving the security binding from the collection, you must cast to one of these types in order to correctly set the `MaxClockSkew` property.</span></span> <span data-ttu-id="d6351-111">L'exemple suivant utilise un <xref:System.ServiceModel.WSHttpBinding>, qui utilise <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="d6351-111">The following example uses a <xref:System.ServiceModel.WSHttpBinding>, which uses the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="d6351-112">Pour obtenir une liste qui spécifie le type de liaison de sécurité à utiliser dans chaque liaison fournie par le système, consultez [liaisons fournies par le système](../system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="d6351-112">For a list that specifies which type of security binding to use in each system-provided binding, see [System-Provided Bindings](../system-provided-bindings.md).</span></span>  
  
## <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a><span data-ttu-id="d6351-113">Pour créer une liaison personnalisée avec une nouvelle valeur d'inclinaison de l'horloge dans du code</span><span class="sxs-lookup"><span data-stu-id="d6351-113">To create a custom binding with a new clock skew value in code</span></span>  
  
> [!WARNING]
> <span data-ttu-id="d6351-114">Ajoutez des références aux espaces de noms suivants dans votre code : <xref:System.ServiceModel.Channels> , <xref:System.ServiceModel.Description> , <xref:System.Security.Permissions> et <xref:System.ServiceModel.Security.Tokens> .</span><span class="sxs-lookup"><span data-stu-id="d6351-114">Add references to the following namespaces in your code: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, and <xref:System.ServiceModel.Security.Tokens>.</span></span>  
  
1. <span data-ttu-id="d6351-115">Créez une instance d'une classe <xref:System.ServiceModel.WSHttpBinding> et choisissez le mode de sécurité <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d6351-115">Create an instance of a <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>.</span></span>  
  
2. <span data-ttu-id="d6351-116">Créez une nouvelle instance de la classe <xref:System.ServiceModel.Channels.BindingElementCollection> en appelant la méthode <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A>.</span><span class="sxs-lookup"><span data-stu-id="d6351-116">Create a new instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class by calling the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3. <span data-ttu-id="d6351-117">Utilisez la méthode <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> de la classe <xref:System.ServiceModel.Channels.BindingElementCollection> pour rechercher l’élément de liaison de sécurité.</span><span class="sxs-lookup"><span data-stu-id="d6351-117">Use the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method of the <xref:System.ServiceModel.Channels.BindingElementCollection> class to find the security binding element.</span></span>  
  
4. <span data-ttu-id="d6351-118">Lorsque vous utilisez la méthode <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A>, effectuez une conversion de type au type réel.</span><span class="sxs-lookup"><span data-stu-id="d6351-118">When using the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method, cast to the actual type.</span></span> <span data-ttu-id="d6351-119">L'exemple suivant effectue une conversion de type au type <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="d6351-119">The example below casts to the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> type.</span></span>  
  
5. <span data-ttu-id="d6351-120">Définissez la propriété <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> sur l’élément de liaison de sécurité.</span><span class="sxs-lookup"><span data-stu-id="d6351-120">Set the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> property on the security binding element.</span></span>  
  
6. <span data-ttu-id="d6351-121">Créez un <xref:System.ServiceModel.ServiceHost> avec un type de service approprié et une adresse de base.</span><span class="sxs-lookup"><span data-stu-id="d6351-121">Create a <xref:System.ServiceModel.ServiceHost> with an appropriate service type and base address.</span></span>  
  
7. <span data-ttu-id="d6351-122">Utilisez la méthode <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> pour ajouter un point de terminaison et inclure la <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="d6351-122">Use the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method to add an endpoint and include the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
## <a name="to-set-the-maxclockskew-in-configuration"></a><span data-ttu-id="d6351-123">Pour définir MaxClockSkew dans la configuration</span><span class="sxs-lookup"><span data-stu-id="d6351-123">To set the MaxClockSkew in configuration</span></span>  
  
1. <span data-ttu-id="d6351-124">Créez un [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) dans la [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) section de l’élément.</span><span class="sxs-lookup"><span data-stu-id="d6351-124">Create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) in the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element section.</span></span>  
  
2. <span data-ttu-id="d6351-125">Créez un [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) élément et affectez `name` à l’attribut une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="d6351-125">Create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="d6351-126">L'exemple suivant lui affecte la valeur `MaxClockSkewBinding`.</span><span class="sxs-lookup"><span data-stu-id="d6351-126">The following example sets it to `MaxClockSkewBinding`.</span></span>  
  
3. <span data-ttu-id="d6351-127">Ajoutez un élément d'encodage.</span><span class="sxs-lookup"><span data-stu-id="d6351-127">Add an encoding element.</span></span> <span data-ttu-id="d6351-128">L’exemple ci-dessous ajoute un [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md) .</span><span class="sxs-lookup"><span data-stu-id="d6351-128">The example below adds a [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
4. <span data-ttu-id="d6351-129">Ajoutez un [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) élément et affectez `authenticationMode` un paramètre approprié à l’attribut.</span><span class="sxs-lookup"><span data-stu-id="d6351-129">Add a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element and set the `authenticationMode` attribute to an appropriate setting.</span></span> <span data-ttu-id="d6351-130">L'exemple suivant affecte à l'attribut la valeur `Kerberos` pour spécifier que le service utilise l'authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="d6351-130">The following example set the attribute to `Kerberos` to specify that the service use Windows authentication.</span></span>  
  
5. <span data-ttu-id="d6351-131">Ajoutez un [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) et affectez `maxClockSkew` à l’attribut une valeur au format `"##:##:##"` .</span><span class="sxs-lookup"><span data-stu-id="d6351-131">Add a [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to a value in the form of `"##:##:##"`.</span></span> <span data-ttu-id="d6351-132">L'exemple suivant lui attribue la valeur 7 minutes.</span><span class="sxs-lookup"><span data-stu-id="d6351-132">The following example sets it to 7 minutes.</span></span> <span data-ttu-id="d6351-133">Si vous le souhaitez, ajoutez un [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) et affectez `maxClockSkew` un paramètre approprié à l’attribut.</span><span class="sxs-lookup"><span data-stu-id="d6351-133">Optionally, add a [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to an appropriate setting.</span></span>  
  
6. <span data-ttu-id="d6351-134">Ajoutez un élément de transport.</span><span class="sxs-lookup"><span data-stu-id="d6351-134">Add a transport element.</span></span> <span data-ttu-id="d6351-135">L’exemple suivant utilise un [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) .</span><span class="sxs-lookup"><span data-stu-id="d6351-135">The following example uses an [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
7. <span data-ttu-id="d6351-136">Pour une conversation sécurisée, les paramètres de sécurité doivent se produire au démarrage de l' [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) élément.</span><span class="sxs-lookup"><span data-stu-id="d6351-136">For a secure conversation, the security settings must occur at the bootstrap in the [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element.</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="MaxClockSkewBinding">  
            <textMessageEncoding />  
            <security authenticationMode="Kerberos">  
               <localClientSettings maxClockSkew="00:07:00" />  
               <localServiceSettings maxClockSkew="00:07:00" />  
               <secureConversationBootstrap>  
                  <localClientSettings maxClockSkew="00:30:00" />  
                  <localServiceSettings maxClockSkew="00:30:00" />  
               </secureConversationBootstrap>  
            </security>  
            <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d6351-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6351-137">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="d6351-138">Procédure : créer une liaison personnalisée à l’aide de SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="d6351-138">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
