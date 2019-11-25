---
title: "Comment : spécifier le type d'informations d'identification du client"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security credentials, adding to SOAP messages
- WCF, security
ms.assetid: 10f51bee-5f92-4c1a-9126-fa5418535d8f
ms.openlocfilehash: df18f89ee18bfa33ecc0aced617d168c805e3515
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74138580"
---
# <a name="how-to-specify-the-client-credential-type"></a><span data-ttu-id="5dd13-102">Comment : spécifier le type d'informations d'identification du client</span><span class="sxs-lookup"><span data-stu-id="5dd13-102">How to: Specify the Client Credential Type</span></span>
<span data-ttu-id="5dd13-103">Après avoir défini un mode de sécurité (transport ou message), vous avez pouvez définir le type d'informations d'identification du client.</span><span class="sxs-lookup"><span data-stu-id="5dd13-103">After setting a security mode (either transport or message), you have the option of setting the client credential type.</span></span> <span data-ttu-id="5dd13-104">Cette propriété spécifie le type d'informations d'identification que le client doit fournir au service dans le cadre de l'authentification.</span><span class="sxs-lookup"><span data-stu-id="5dd13-104">This property specifies what type of credential the client must provide to the service for authentication.</span></span> <span data-ttu-id="5dd13-105">Pour plus d’informations sur la définition du mode de sécurité (étape nécessaire avant de définir le type d’informations d’identification du client), consultez [Comment : définir le mode de sécurité](how-to-set-the-security-mode.md).</span><span class="sxs-lookup"><span data-stu-id="5dd13-105">For more information about setting the security mode (a necessary step before setting the client credential type), see [How to: Set the Security Mode](how-to-set-the-security-mode.md).</span></span>  
  
### <a name="to-set-the-client-credential-type-in-code"></a><span data-ttu-id="5dd13-106">Pour définir le type d'informations d'identification du client dans le code</span><span class="sxs-lookup"><span data-stu-id="5dd13-106">To set the client credential type in code</span></span>  
  
1. <span data-ttu-id="5dd13-107">Créez une instance de la liaison que le service utilisera.</span><span class="sxs-lookup"><span data-stu-id="5dd13-107">Create an instance of the binding that the service will use.</span></span> <span data-ttu-id="5dd13-108">Cet exemple utilise la liaison <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="5dd13-108">This example uses the <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>  
  
2. <span data-ttu-id="5dd13-109">Affectez à la propriété <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="5dd13-109">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to an appropriate value.</span></span> <span data-ttu-id="5dd13-110">Cet exemple utilise le mode de message.</span><span class="sxs-lookup"><span data-stu-id="5dd13-110">This example uses the Message mode.</span></span>  
  
3. <span data-ttu-id="5dd13-111">Affectez à la propriété <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="5dd13-111">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="5dd13-112">Dans notre exemple, la propriété est définie de sorte à utiliser l'authentification Windows (<xref:System.ServiceModel.MessageCredentialType.Windows>).</span><span class="sxs-lookup"><span data-stu-id="5dd13-112">This example sets it to use Windows authentication (<xref:System.ServiceModel.MessageCredentialType.Windows>).</span></span>  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a><span data-ttu-id="5dd13-113">Pour définir le type d'informations d'identification du client dans la configuration</span><span class="sxs-lookup"><span data-stu-id="5dd13-113">To set the client credential type in configuration</span></span>  
  
1. <span data-ttu-id="5dd13-114">Ajoutez un [\<élément System. serviceModel >](../configure-apps/file-schema/wcf/system-servicemodel.md) au fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="5dd13-114">Add a [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) element to the configuration file.</span></span>  
  
2. <span data-ttu-id="5dd13-115">En tant qu’élément enfant, ajoutez une [\<liaisons >](../configure-apps/file-schema/wcf/bindings.md) élément.</span><span class="sxs-lookup"><span data-stu-id="5dd13-115">As a child element, add a [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
3. <span data-ttu-id="5dd13-116">Ajoutez une liaison appropriée.</span><span class="sxs-lookup"><span data-stu-id="5dd13-116">Add an appropriate binding.</span></span> <span data-ttu-id="5dd13-117">Cet exemple utilise l’élément [\<wsHttpBinding >](../configure-apps/file-schema/wcf/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="5dd13-117">This example uses the [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>  
  
4. <span data-ttu-id="5dd13-118">Ajoutez un élément de [> de liaison\<](../configure-apps/file-schema/wcf/bindings.md) et définissez l’attribut `name` sur une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="5dd13-118">Add a [\<binding>](../configure-apps/file-schema/wcf/bindings.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="5dd13-119">Cet exemple utilise le nom « SecureBinding ».</span><span class="sxs-lookup"><span data-stu-id="5dd13-119">This example uses the name "SecureBinding".</span></span>  
  
5. <span data-ttu-id="5dd13-120">Ajoutez une liaison `<security>`.</span><span class="sxs-lookup"><span data-stu-id="5dd13-120">Add a `<security>` binding.</span></span> <span data-ttu-id="5dd13-121">Affectez la valeur appropriée à l'attribut `mode`.</span><span class="sxs-lookup"><span data-stu-id="5dd13-121">Set the `mode` attribute to an appropriate value.</span></span> <span data-ttu-id="5dd13-122">Cet exemple lui affecte la valeur `"Message"`.</span><span class="sxs-lookup"><span data-stu-id="5dd13-122">This example sets it to `"Message"`.</span></span>  
  
6. <span data-ttu-id="5dd13-123">Ajoutez un élément `<message>` ou un élément `<transport>` comme requis par le mode de sécurité.</span><span class="sxs-lookup"><span data-stu-id="5dd13-123">Add either a `<message>` or `<transport>` element, as determined by the security mode.</span></span> <span data-ttu-id="5dd13-124">Affectez la valeur appropriée à l'attribut `clientCredentialType`.</span><span class="sxs-lookup"><span data-stu-id="5dd13-124">Set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="5dd13-125">Cet exemple utilise `"Windows"`.</span><span class="sxs-lookup"><span data-stu-id="5dd13-125">This example uses `"Windows"`.</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="SecureBinding">  
            <security mode="Message">  
                 <message clientCredentialType="Windows" />  
             </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
    </system.serviceModel>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5dd13-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5dd13-126">See also</span></span>

- [<span data-ttu-id="5dd13-127">Sécurisation de services</span><span class="sxs-lookup"><span data-stu-id="5dd13-127">Securing Services</span></span>](securing-services.md)
- [<span data-ttu-id="5dd13-128">Guide pratique pour définir le mode de sécurité</span><span class="sxs-lookup"><span data-stu-id="5dd13-128">How to: Set the Security Mode</span></span>](how-to-set-the-security-mode.md)
