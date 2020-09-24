---
title: <bindingElementExtensions>
ms.date: 03/30/2017
ms.assetid: bb597fc0-c947-451c-afda-bf23d42f4f4d
ms.openlocfilehash: 6ba97adfa696e00b4d6b75faf104c31436e25447
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151128"
---
# \<bindingElementExtensions>

<span data-ttu-id="f63ca-101">Cette section active l'utilisation d'un élément de liaison personnalisé à partir d'un ordinateur ou d'un fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="f63ca-101">This section enables the use of a custom binding element from a machine or application configuration file.</span></span> <span data-ttu-id="f63ca-102">Vous pouvez ajouter un élément de liaison personnalisé à cette collection en utilisant le mot clé `add` et affecter à l’attribut `type` de l’élément une extension d’élément de liaison, ainsi que l’attribut `name` à l’élément de liaison personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f63ca-102">You can add a custom binding element to this collection by using the `add` keyword, and setting the `type` attribute of the element to a binding element extension, as well as the `name` attribute to the custom binding element.</span></span>  
  
 <span data-ttu-id="f63ca-103">Les extensions de liaison permettent la création d’éléments de liaison définis par l’utilisateur à utiliser dans le cadre de liaisons personnalisées.</span><span class="sxs-lookup"><span data-stu-id="f63ca-103">Binding extensions enable the user to create user-defined binding elements for use as part of custom bindings.</span></span> <span data-ttu-id="f63ca-104">Par programme, une extension de liaison est un type qui implémente la classe abstraite <xref:System.ServiceModel.Channels.BindingElement>.</span><span class="sxs-lookup"><span data-stu-id="f63ca-104">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.BindingElement>.</span></span> <span data-ttu-id="f63ca-105">Dans le fichier de configuration, la section `bindingElementExtensions` est utilisée pour définir un élément d’extension.</span><span class="sxs-lookup"><span data-stu-id="f63ca-105">In the configuration file, the `bindingElementExtensions` section is used to define an extension element.</span></span>  
  
 <span data-ttu-id="f63ca-106">L'exemple suivant utilise l'élément `add` ainsi que l'attribut `name` pour ajouter une extension de liaison à la section `bindingElementExtensions` du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="f63ca-106">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
```xml  
<system.serviceModel>
  <extensions>
    <bindingElementExtensions>
      <add name="udpTransport"
           type="Microsoft.ServiceModel.Samples.UdpTransportSection, UdpTransport,
                 Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
    </bindingElementExtensions>
  </extensions>
</system.serviceModel>
```  
  
 <span data-ttu-id="f63ca-107">Pour ajouter des capacités de configuration à l'élément, l'utilisateur doit écrire et enregistrer un élément `bindingElementExtensionSection`.</span><span class="sxs-lookup"><span data-stu-id="f63ca-107">To add configuration abilities to the element, the user needs to write and register a `bindingElementExtensionSection` element.</span></span> <span data-ttu-id="f63ca-108">Pour plus d'informations, consultez la documentation <xref:System.Configuration>.</span><span class="sxs-lookup"><span data-stu-id="f63ca-108">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="f63ca-109">Après la définition de l’élément et de son type de configuration, l’extension peut être utilisée comme une partie de la liaison personnalisée telle que présentée dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="f63ca-109">After the element and its configuration type are defined, the extension can be used as part of a custom binding as shown in the following example.</span></span>  
  
```xml  
<customBinding>
  <binding name="test2">
    <udpTransport />
    <binaryMessageEncoding maxReadPoolSize="211"
                           maxWritePoolSize="2132"
                           maxSessionSize="3141" />
  </binding>
</customBinding>
```  
  
## <a name="see-also"></a><span data-ttu-id="f63ca-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f63ca-110">See also</span></span>

- <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>
- [<span data-ttu-id="f63ca-111">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="f63ca-111">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
