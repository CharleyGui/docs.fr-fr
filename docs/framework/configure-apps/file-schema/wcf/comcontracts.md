---
title: <comContracts>
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: 404cc66ce423ba947c2817b56bebb4daf341ef0b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176043"
---
# \<comContracts>

<span data-ttu-id="c27eb-101">La section de configuration `comContracts` contient des éléments qui vous permettent de spécifier différentes propriétés d'un contrat de service d'intégration COM+.</span><span class="sxs-lookup"><span data-stu-id="c27eb-101">The `comContracts` configuration section contains elements that allow you to specify various properties of a COM+ integration service contract.</span></span>  
  
## <a name="specifying-namespace-and-contract"></a><span data-ttu-id="c27eb-102">Spécification d'espace de noms et de contrat</span><span class="sxs-lookup"><span data-stu-id="c27eb-102">Specifying Namespace and Contract</span></span>  

 <span data-ttu-id="c27eb-103">Les contrats de service d’intégration COM+ sont actuellement restreints à l' `http://tempuri.org` espace de noms et le nom de contrat est dérivé de l’interface com de prise en charge.</span><span class="sxs-lookup"><span data-stu-id="c27eb-103">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="c27eb-104">Toutefois, vous pouvez en spécifier d'autres à l'aide de la section `comContracts` du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="c27eb-104">You can, however, specify alternatives by using the `comContracts` section in the configuration file.</span></span>  
  
 <span data-ttu-id="c27eb-105">Par exemple, vous pouvez utiliser la configuration suivante pour spécifier l’espace de noms et le nom du contrat de service, aussi bien qu’une option pour mettre en vigueur l’utilisation sur les liaisons de session.</span><span class="sxs-lookup"><span data-stu-id="c27eb-105">For example, you can use the following configuration to specify the namespace and contract name of the service contract, as well as an option to enforce usage on sessionful bindings.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
  </comContract>
</comContracts>
```  
  
 <span data-ttu-id="c27eb-106">Lorsque le service est initialisé, les espaces de noms et les noms de contrat spécifiés sont appliqués aux descriptions de service générées.</span><span class="sxs-lookup"><span data-stu-id="c27eb-106">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
 <span data-ttu-id="c27eb-107">Lorsque cette section est vide, l'initialisation de service applique un espace de noms et un nom de contrat par défaut à partir de l'ID d'interface COM de prise en charge.</span><span class="sxs-lookup"><span data-stu-id="c27eb-107">When this section is empty, the service initialization applies a default namespace and contract name taken from the supporting COM interface ID.</span></span>  
  
 <span data-ttu-id="c27eb-108">En outre, vous pouvez utiliser l' [\<exposedMethod>](exposedmethod.md) élément pour spécifier des méthodes com+ exposées lorsque l’interface sur un composant com+ est exposée en tant que service Web.</span><span class="sxs-lookup"><span data-stu-id="c27eb-108">In addition, you can use the [\<exposedMethod>](exposedmethod.md) element to specify COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span> <span data-ttu-id="c27eb-109">Vous pouvez également utiliser le [\<persistableTypes>](persistabletypes.md) pour spécifier les types persistants utilisés dans l’intégration.</span><span class="sxs-lookup"><span data-stu-id="c27eb-109">You can also use the [\<persistableTypes>](persistabletypes.md) to specify persistable types used in integration.</span></span> <span data-ttu-id="c27eb-110">Enfin, vous pouvez utiliser l' [\<userDefinedType>](userdefinedtype.md) élément pour inclure des types définis par l’utilisateur (UDT) qui doivent être inclus dans le contrat de service.</span><span class="sxs-lookup"><span data-stu-id="c27eb-110">Finally, you can use the [\<userDefinedType>](userdefinedtype.md) element to include User Defined Types (UDT) that are to be included in the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c27eb-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c27eb-111">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [\<exposedMethod>](exposedmethod.md)
- [\<persistableTypes>](persistabletypes.md)
- [\<userDefinedType>](userdefinedtype.md)
- [\<comContract>](comcontract.md)
- [<span data-ttu-id="c27eb-112">Intégration à des applications COM+</span><span class="sxs-lookup"><span data-stu-id="c27eb-112">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="c27eb-113">Procédure : configurer des paramètres de service COM+</span><span class="sxs-lookup"><span data-stu-id="c27eb-113">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
