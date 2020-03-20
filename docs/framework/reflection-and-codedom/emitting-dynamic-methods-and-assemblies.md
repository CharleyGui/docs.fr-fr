---
title: Émission d'assemblys et de méthodes dynamiques
ms.date: 08/30/2017
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
ms.openlocfilehash: fda5a20eb7798086ec10415889454b4a8beba5f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180524"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a><span data-ttu-id="0016d-102">Émission d'assemblys et de méthodes dynamiques</span><span class="sxs-lookup"><span data-stu-id="0016d-102">Emitting Dynamic Methods and Assemblies</span></span>

<span data-ttu-id="0016d-103">Cette section décrit un ensemble de types managés dans l'espace de noms <xref:System.Reflection.Emit>, qui permettent à un compilateur ou à un outil d'émettre des métadonnées et du langage MSIL (Microsoft Intermediate Language) au moment de l'exécution et de générer éventuellement un fichier exécutable portable sur le disque.</span><span class="sxs-lookup"><span data-stu-id="0016d-103">This section describes a set of managed types in the <xref:System.Reflection.Emit> namespace that allow a compiler or tool to emit metadata and Microsoft intermediate language (MSIL) at run time and optionally generate a portable executable (PE) file on disk.</span></span> <span data-ttu-id="0016d-104">Les moteurs de script et les compilateurs sont les principaux utilisateurs de cet espace de noms.</span><span class="sxs-lookup"><span data-stu-id="0016d-104">Script engines and compilers are the primary users of this namespace.</span></span> <span data-ttu-id="0016d-105">Dans cette section, la fonctionnalité fournies par l'espace de noms <xref:System.Reflection.Emit> est appelée émission de réflexion.</span><span class="sxs-lookup"><span data-stu-id="0016d-105">In this section, the functionality provided by the <xref:System.Reflection.Emit> namespace is referred to as reflection emit.</span></span>  
  
<span data-ttu-id="0016d-106">L'émission de réflexion offre les possibilités suivantes :</span><span class="sxs-lookup"><span data-stu-id="0016d-106">Reflection emit provides the following capabilities:</span></span>  
  
- <span data-ttu-id="0016d-107">Définir des méthodes globales légères au moment de l'exécution à l'aide de la classe <xref:System.Reflection.Emit.DynamicMethod>, et les exécuter à l'aide de délégués.</span><span class="sxs-lookup"><span data-stu-id="0016d-107">Define lightweight global methods at run time, using the <xref:System.Reflection.Emit.DynamicMethod> class, and execute them using delegates.</span></span>  
  
- <span data-ttu-id="0016d-108">Définir des assemblys au moment de l'exécution, puis les exécuter et/ou les enregistrer sur disque.</span><span class="sxs-lookup"><span data-stu-id="0016d-108">Define assemblies at run time and then run them and/or save them to disk.</span></span>  
  
- <span data-ttu-id="0016d-109">Définir des assemblys au moment de l'exécution, les exécuter, puis les décharger et autoriser le garbage collection à libérer leurs ressources.</span><span class="sxs-lookup"><span data-stu-id="0016d-109">Define assemblies at run time, run them, and then unload them and allow garbage collection to reclaim their resources.</span></span>  
  
- <span data-ttu-id="0016d-110">Définir des modules dans de nouveaux assemblys au moment de l'exécution, puis les exécuter et/ou les enregistrer sur disque.</span><span class="sxs-lookup"><span data-stu-id="0016d-110">Define modules in new assemblies at run time and then run and/or save them to disk.</span></span>  
  
- <span data-ttu-id="0016d-111">Définir des types dans des modules au moment de l'exécution, créer des instances de ces types et appeler leurs méthodes.</span><span class="sxs-lookup"><span data-stu-id="0016d-111">Define types in modules at run time, create instances of these types, and invoke their methods.</span></span>  
  
- <span data-ttu-id="0016d-112">Définir des informations symboliques pour des modules définis, qui peut être utilisées par des outils comme des débogueurs et des profileurs de code.</span><span class="sxs-lookup"><span data-stu-id="0016d-112">Define symbolic information for defined modules that can be used by tools such as debuggers and code profilers.</span></span>  
  
<span data-ttu-id="0016d-113">En plus des types managés dans l’espace de noms <xref:System.Reflection.Emit>, il existe des interfaces de métadonnées non managées qui sont décrites dans la documentation de référence [Interfaces de métadonnées](../unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="0016d-113">In addition to the managed types in the <xref:System.Reflection.Emit> namespace, there are unmanaged metadata interfaces which are described in the [Metadata Interfaces](../unmanaged-api/metadata/metadata-interfaces.md) reference documentation.</span></span> <span data-ttu-id="0016d-114">L'émission de réflexion managée offre une vérification des erreurs sémantiques plus puissante et un niveau d'abstraction des métadonnées plus élevé que les interfaces de métadonnées non managées.</span><span class="sxs-lookup"><span data-stu-id="0016d-114">Managed reflection emit provides stronger semantic error checking and a higher level of abstraction of the metadata than the unmanaged metadata interfaces.</span></span>  
  
<span data-ttu-id="0016d-115">Une autre ressource utile pour travailler avec les métadonnées et MSIL est la documentation de la Common Language Infrastructure (CLI), en particulier "Partie II : définition et sémantique des métadonnées" et "Partie III : jeu d'instructions de CIL".</span><span class="sxs-lookup"><span data-stu-id="0016d-115">Another useful resource for working with metadata and MSIL is the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="0016d-116">La documentation est disponible en ligne sur le [site Web d’Ecma](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="0016d-116">The documentation is available online at the [Ecma Web site](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0016d-117">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="0016d-117">In This Section</span></span>
  
[<span data-ttu-id="0016d-118">Les questions de sécurité dans la réflexion émettent</span><span class="sxs-lookup"><span data-stu-id="0016d-118">Security issues in reflection emit</span></span>](security-issues-in-reflection-emit.md)  
<span data-ttu-id="0016d-119">Décrit les problèmes de sécurité liés à la création d'assemblys dynamiques en utilisant l'émission de réflexion.</span><span class="sxs-lookup"><span data-stu-id="0016d-119">Describes security issues related to creating dynamic assemblies using reflection emit.</span></span>  

<span data-ttu-id="0016d-120">[Comment : Définir et exécuter des méthodes dynamiques](how-to-define-and-execute-dynamic-methods.md) Montre comment exécuter une méthode dynamique simple et une méthode dynamique liée à une instance d’une classe.</span><span class="sxs-lookup"><span data-stu-id="0016d-120">[How to: Define and execute dynamic methods](how-to-define-and-execute-dynamic-methods.md) Shows how to execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>

<span data-ttu-id="0016d-121">[Comment : Définir un type générique avec l’émission de réflexion](how-to-define-a-generic-type-with-reflection-emit.md) Montre comment créer un type générique simple avec deux paramètres de type, comment appliquer la classe, l’interface, et des contraintes spéciales aux paramètres de type, et comment créer des membres qui utilisent les paramètres de type de la classe comme types de paramètres et de types de retour.</span><span class="sxs-lookup"><span data-stu-id="0016d-121">[How to: Define a generic type with reflection emit](how-to-define-a-generic-type-with-reflection-emit.md) Shows how to create a simple generic type with two type parameters, how to apply class, interface, and special constraints to the type parameters, and how to create members that use the type parameters of the class as parameter types and return types.</span></span>

<span data-ttu-id="0016d-122">[Comment : Définir une méthode générique avec l’émission de réflexion](how-to-define-a-generic-method-with-reflection-emit.md) Montre comment créer, émettre et invoquer une méthode générique simple.</span><span class="sxs-lookup"><span data-stu-id="0016d-122">[How to: Define a generic method with reflection emit](how-to-define-a-generic-method-with-reflection-emit.md) Shows how to create, emit, and invoke a simple generic method.</span></span>

<span data-ttu-id="0016d-123">[Assemblages collectibles pour la génération de type dynamique](collectible-assemblies.md) Introduit des assemblages de collection, qui sont des assemblages dynamiques qui peuvent être déchargés sans décharger le domaine d’application dans lequel ils ont été créés.</span><span class="sxs-lookup"><span data-stu-id="0016d-123">[Collectible assemblies for dynamic type generation](collectible-assemblies.md) Introduces collectible assemblies, which are dynamic assemblies that can be unloaded without unloading the application domain in which they were created.</span></span>
  
## <a name="reference"></a><span data-ttu-id="0016d-124">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="0016d-124">Reference</span></span>  

<xref:System.Reflection.Emit.OpCodes>  
<span data-ttu-id="0016d-125">Répertorie les codes des instructions MSIL que vous pouvez utiliser pour créer des corps de méthode.</span><span class="sxs-lookup"><span data-stu-id="0016d-125">Catalogs the MSIL instruction codes you can use to build method bodies.</span></span>  
  
<xref:System.Reflection.Emit>  
<span data-ttu-id="0016d-126">Contient des classes managées utilisées pour émettre des méthodes, des assemblys et des types dynamiques.</span><span class="sxs-lookup"><span data-stu-id="0016d-126">Contains managed classes used to emit dynamic methods, assemblies, and types.</span></span>  
  
<xref:System.Type>  
<span data-ttu-id="0016d-127">Décrit la classe <xref:System.Type>, qui représente des types dans la réflexion managée et dans l'émission de réflexion, et qui est essentielle dans l'utilisation de ces technologies.</span><span class="sxs-lookup"><span data-stu-id="0016d-127">Describes the <xref:System.Type> class, which represents types in managed reflection and reflection emit, and which is key to the use of these technologies.</span></span>  
  
<xref:System.Reflection>  
<span data-ttu-id="0016d-128">Contient des classes managées utilisées pour explorer les métadonnées et le code managé.</span><span class="sxs-lookup"><span data-stu-id="0016d-128">Contains managed classes used to explore metadata and managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0016d-129">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="0016d-129">Related Sections</span></span>  

[<span data-ttu-id="0016d-130">Réflexion</span><span class="sxs-lookup"><span data-stu-id="0016d-130">Reflection</span></span>](reflection.md)  
<span data-ttu-id="0016d-131">Explique comment explorer les métadonnées et le code managé.</span><span class="sxs-lookup"><span data-stu-id="0016d-131">Explains how to explore metadata and managed code.</span></span>  
  
[<span data-ttu-id="0016d-132">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="0016d-132">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="0016d-133">Fournit une vue d’ensemble des assemblys dans les implémentations de .NET.</span><span class="sxs-lookup"><span data-stu-id="0016d-133">Provides an overview of assemblies in .NET implementations.</span></span>
