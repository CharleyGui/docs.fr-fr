---
title: Règles de documentation (analyse du code)
description: En savoir plus sur les règles de documentation des règles d’analyse du code
ms.date: 09/16/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.documentationrules
helpviewer_keywords:
- documentation rules
- managed code analysis rules, documentation rules
- warnings, documentation
author: mavasani
ms.author: mavasani
ms.openlocfilehash: 29d1734eec29bd00d456b4b00c48c2e8ef223441
ms.sourcegitcommit: 2e4adc490c1d2a705a0592b295d606b10b9f51f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "96587218"
---
# <a name="documentation-rules"></a><span data-ttu-id="014f8-103">Règles de documentation</span><span class="sxs-lookup"><span data-stu-id="014f8-103">Documentation rules</span></span>

<span data-ttu-id="014f8-104">Les règles de documentation prennent en charge l’écriture de bibliothèques bien documentées via l’utilisation correcte des [Commentaires de documentation XML](../../../csharp/codedoc.md) pour les API visibles de l’extérieur.</span><span class="sxs-lookup"><span data-stu-id="014f8-104">Documentation rules support writing well-documented libraries through the correct use of [XML documentation comments](../../../csharp/codedoc.md) for externally visible APIs.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="014f8-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="014f8-105">In this section</span></span>

| <span data-ttu-id="014f8-106">Règle</span><span class="sxs-lookup"><span data-stu-id="014f8-106">Rule</span></span> | <span data-ttu-id="014f8-107">Description</span><span class="sxs-lookup"><span data-stu-id="014f8-107">Description</span></span> |
| - | - |
| [<span data-ttu-id="014f8-108">CA1200 : Éviter d’utiliser des balises cref avec un préfixe</span><span class="sxs-lookup"><span data-stu-id="014f8-108">CA1200: Avoid using cref tags with a prefix</span></span>](ca1200.md) | <span data-ttu-id="014f8-109">L’attribut [cref](../../../csharp/programming-guide/xmldoc/cref-attribute.md) dans une balise de documentation XML signifie « référence du code ».</span><span class="sxs-lookup"><span data-stu-id="014f8-109">The [cref](../../../csharp/programming-guide/xmldoc/cref-attribute.md) attribute in an XML documentation tag means "code reference".</span></span> <span data-ttu-id="014f8-110">Il indique que le texte interne de la balise est un élément de code tel qu’un type, une méthode ou une propriété.</span><span class="sxs-lookup"><span data-stu-id="014f8-110">It specifies that the inner text of the tag is a code element, such as a type, method, or property.</span></span> <span data-ttu-id="014f8-111">Évitez `cref` d’utiliser des balises avec des préfixes, car cela empêche le compilateur de vérifier les références.</span><span class="sxs-lookup"><span data-stu-id="014f8-111">Avoid using `cref` tags with prefixes, because it prevents the compiler from verifying references.</span></span> <span data-ttu-id="014f8-112">Cela empêche également l’environnement de développement intégré (IDE) de Visual Studio de rechercher et de mettre à jour ces références de symboles lors des refactorisations.</span><span class="sxs-lookup"><span data-stu-id="014f8-112">It also prevents the Visual Studio integrated development environment (IDE) from finding and updating these symbol references during refactorings.</span></span> |
