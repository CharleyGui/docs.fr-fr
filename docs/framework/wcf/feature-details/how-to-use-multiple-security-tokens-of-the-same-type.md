---
title: 'Procédure : utiliser plusieurs jetons de sécurité du même type'
ms.date: 03/30/2017
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
ms.openlocfilehash: 1b383c6ccd96d1b3d7b091b2d7c67bb166da51df
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65589422"
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="89cf0-102">Procédure : utiliser plusieurs jetons de sécurité du même type</span><span class="sxs-lookup"><span data-stu-id="89cf0-102">How to: Use Multiple Security Tokens of the Same Type</span></span>
- <span data-ttu-id="89cf0-103">Dans .NET Framework 3.0, un message client ne contenait qu’un seul jeton d’un type donné.</span><span class="sxs-lookup"><span data-stu-id="89cf0-103">In .NET Framework 3.0, a client message only contained one token of any given type.</span></span> <span data-ttu-id="89cf0-104">Désormais, les messages peuvent contenir plusieurs jetons d'un type donné.</span><span class="sxs-lookup"><span data-stu-id="89cf0-104">Now client messages can contain multiple tokens of a type.</span></span> <span data-ttu-id="89cf0-105">Cette rubrique explique comment inclure plusieurs jetons du même type dans un message client.</span><span class="sxs-lookup"><span data-stu-id="89cf0-105">This topic shows how to include multiple tokens of the same type in a client message.</span></span>  
  
- <span data-ttu-id="89cf0-106">Notez que vous ne pouvez pas configurer un service ainsi : un service peut contenir un seul jeton de prise en charge.</span><span class="sxs-lookup"><span data-stu-id="89cf0-106">Note that you cannot configure a service in this way: a service can contain only one supporting token.</span></span>  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="89cf0-107">Pour utiliser plusieurs jetons de sécurité du même type</span><span class="sxs-lookup"><span data-stu-id="89cf0-107">To use multiple security tokens of the same type</span></span>  
  
1. <span data-ttu-id="89cf0-108">Créez une collection d'éléments de liaison vide à remplir.</span><span class="sxs-lookup"><span data-stu-id="89cf0-108">Create an empty binding element collection to be populated.</span></span>  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2. <span data-ttu-id="89cf0-109">Créez un <xref:System.ServiceModel.Channels.SecurityBindingElement> en appelant <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="89cf0-109">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> by calling <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span></span>  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3. <span data-ttu-id="89cf0-110">Créez une collection <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters>.</span><span class="sxs-lookup"><span data-stu-id="89cf0-110">Create a <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4. <span data-ttu-id="89cf0-111">Ajoutez des jetons SAML à la collection.</span><span class="sxs-lookup"><span data-stu-id="89cf0-111">Add SAML tokens to the collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5. <span data-ttu-id="89cf0-112">Ajoutez la collection à <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="89cf0-112">Add the collection to the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6. <span data-ttu-id="89cf0-113">Ajoutez des éléments de liaison à la collection d'éléments de liaison.</span><span class="sxs-lookup"><span data-stu-id="89cf0-113">Add binding elements to the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7. <span data-ttu-id="89cf0-114">Retournez une nouvelle liaison personnalisée créée à partir de la collection d'éléments de liaison.</span><span class="sxs-lookup"><span data-stu-id="89cf0-114">Return a new custom binding created from the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a><span data-ttu-id="89cf0-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="89cf0-115">Example</span></span>  
 <span data-ttu-id="89cf0-116">Vous trouverez ci-dessous la méthode complète décrite par la procédure précédente.</span><span class="sxs-lookup"><span data-stu-id="89cf0-116">The following is the entire method described by the preceding procedure.</span></span>  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  
