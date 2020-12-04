---
title: Règles de portabilité et d’interopérabilité (analyse du code)
description: En savoir plus sur les règles de portabilité et d’interopérabilité des règles d’analyse du code
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Portablityrules
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis rules, interoperability rules, portability rules
- portability rules
- warnings, portability
- interoperability rules
- warnings, interoperability
author: gewarren
ms.author: gewarren
ms.openlocfilehash: a20cd77e13c4a8b95633d129990667f0a8de3ee8
ms.sourcegitcommit: 2e4adc490c1d2a705a0592b295d606b10b9f51f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "96586965"
---
# <a name="portability-and-interoperability-rules"></a><span data-ttu-id="b5afc-103">Règles de portabilité et d’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="b5afc-103">Portability and interoperability rules</span></span>

<span data-ttu-id="b5afc-104">Les règles de portabilité prennent en charge la portabilité sur différentes plateformes.</span><span class="sxs-lookup"><span data-stu-id="b5afc-104">Portability rules support portability across different platforms.</span></span> <span data-ttu-id="b5afc-105">Les règles d’interopérabilité prennent en charge l’interaction avec les clients COM.</span><span class="sxs-lookup"><span data-stu-id="b5afc-105">Interoperability rules support interaction with COM clients.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="b5afc-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="b5afc-106">In this section</span></span>

| <span data-ttu-id="b5afc-107">Règle</span><span class="sxs-lookup"><span data-stu-id="b5afc-107">Rule</span></span> | <span data-ttu-id="b5afc-108">Description</span><span class="sxs-lookup"><span data-stu-id="b5afc-108">Description</span></span> |
| - | - |
| [<span data-ttu-id="b5afc-109">Ca1401 : les P/Invoke ne doivent pas être visibles</span><span class="sxs-lookup"><span data-stu-id="b5afc-109">CA1401: P/Invokes should not be visible</span></span>](ca1401.md) | <span data-ttu-id="b5afc-110">Une méthode publique ou protégée dans un type public a l’attribut System.Runtime.InteropServices.DllImportAttribute (également implémenté par le mot clé Declare dans Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="b5afc-110">A public or protected method in a public type has the System.Runtime.InteropServices.DllImportAttribute attribute (also implemented by the Declare keyword in Visual Basic).</span></span> <span data-ttu-id="b5afc-111">De telles méthodes ne doivent pas être exposées.</span><span class="sxs-lookup"><span data-stu-id="b5afc-111">Such methods should not be exposed.</span></span> |
| [<span data-ttu-id="b5afc-112">CA1416 : Valider la compatibilité de la plateforme</span><span class="sxs-lookup"><span data-stu-id="b5afc-112">CA1416: Validate platform compatibility</span></span>](ca1416.md) | <span data-ttu-id="b5afc-113">L’utilisation d’API dépendant de la plateforme sur un composant rend le code ne plus fonctionner sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="b5afc-113">Using platform-dependent APIs on a component makes the code no longer work across all platforms.</span></span> |
| [<span data-ttu-id="b5afc-114">Ca1417 : ne pas utiliser `OutAttribute` sur les paramètres de chaîne pour les P/Invoke</span><span class="sxs-lookup"><span data-stu-id="b5afc-114">CA1417: Do not use `OutAttribute` on string parameters for P/Invokes</span></span>](ca1417.md) | <span data-ttu-id="b5afc-115">Les paramètres de chaîne passés par valeur avec le `OutAttribute` peuvent déstabiliser le runtime si la chaîne est une chaîne internée.</span><span class="sxs-lookup"><span data-stu-id="b5afc-115">String parameters passed by value with the `OutAttribute` can destabilize the runtime if the string is an interned string.</span></span> |
