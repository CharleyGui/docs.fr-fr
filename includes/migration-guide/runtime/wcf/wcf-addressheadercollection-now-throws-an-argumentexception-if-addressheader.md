---
ms.openlocfilehash: e8b98e465228afd07432e737bb16aefb1b979973
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770913"
---
### <a name="wcf-addressheadercollection-now-throws-an-argumentexception-if-an-addressheader-element-is-null"></a><span data-ttu-id="b8569-101">AddressHeaderCollection dans WCF lève maintenant une exception ArgumentException si un élément addressHeader a la valeur Null</span><span class="sxs-lookup"><span data-stu-id="b8569-101">WCF AddressHeaderCollection now throws an ArgumentException if an addressHeader element is null</span></span>

#### <a name="details"></a><span data-ttu-id="b8569-102">Détails</span><span class="sxs-lookup"><span data-stu-id="b8569-102">Details</span></span>

<span data-ttu-id="b8569-103">À compter de .NET Framework 4.7.1, le constructeur <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> lève une <xref:System.ArgumentException> si l’un des éléments a la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="b8569-103">Starting with the .NET Framework 4.7.1, the <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> constructor throws an <xref:System.ArgumentException> if one of the elements is `null`.</span></span> <span data-ttu-id="b8569-104">Dans .NET Framework 4.7 et versions antérieures, aucune exception n’est levée.</span><span class="sxs-lookup"><span data-stu-id="b8569-104">In the .NET Framework 4.7 and earlier versions, no exception is thrown.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b8569-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="b8569-105">Suggestion</span></span>

<span data-ttu-id="b8569-106">Si vous rencontrez des problèmes de compatibilité avec cette modification sur le .NET Framework 4.7.1 ou une version ultérieure, vous pouvez choisir de l’annuler en ajoutant la ligne suivante à la `<runtime>` section du fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="b8569-106">If you encounter compatibility issues with this change on the .NET Framework 4.7.1 or a later version, you can opt-out of it by adding the following line to the `<runtime>` section of the app.config file:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableAddressHeaderCollectionValidation=true" />
  </runtime>
</configuration>

| Name    | Value   |
|:--------|:--------|
| Scope   | Minor   |
| Version | 4.7.1   |
| Type    | Runtime |

#### Affected APIs

- <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})>

<!--

#### Affected APIs

- `M:System.ServiceModel.Channels.AddressHeaderCollection.#ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})`

-->
