---
title: 'Procédure : générer des assemblys d’interopérabilité à partir de bibliothèques de types'
description: Générer des assemblys d’interopérabilité à partir de bibliothèques de types. Utilisez l’importateur de bibliothèques de types (Tlbimp.exe) pour convertir les coclasses et les interfaces d’une bibliothèque de types COM en métadonnées.
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- Type Library Importer
- type libraries
- COM interop, importing type library
ms.assetid: 4afd40c3-68f2-41c5-8ec1-4951bc148b9c
ms.openlocfilehash: 3146d607392a590974f452e06eb5a8b125e58e69
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236362"
---
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a><span data-ttu-id="5b4c9-104">Procédure : générer des assemblys d’interopérabilité à partir de bibliothèques de types</span><span class="sxs-lookup"><span data-stu-id="5b4c9-104">How to: Generate Interop Assemblies from Type Libraries</span></span>

<span data-ttu-id="5b4c9-105">L’outil en ligne de commande [Tlbimp.exe (importateur de bibliothèques de types)](../tools/tlbimp-exe-type-library-importer.md) permet de convertir les coclasses et les interfaces figurant dans une bibliothèque de types COM en métadonnées.</span><span class="sxs-lookup"><span data-stu-id="5b4c9-105">The [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) is a command-line tool that converts the coclasses and interfaces contained in a COM type library to metadata.</span></span> <span data-ttu-id="5b4c9-106">Cet outil crée automatiquement un assembly d’interopérabilité et un espace de noms pour les informations sur les types.</span><span class="sxs-lookup"><span data-stu-id="5b4c9-106">This tool creates an interop assembly and namespace for the type information automatically.</span></span> <span data-ttu-id="5b4c9-107">Une fois les métadonnées d’une classe disponibles, les clients managés peuvent créer des instances du type COM et appeler ses méthodes, comme s’il s’agissait d’une instance .NET.</span><span class="sxs-lookup"><span data-stu-id="5b4c9-107">After the metadata of a class is available, managed clients can create instances of the COM type and call its methods, just as if it were a .NET instance.</span></span> <span data-ttu-id="5b4c9-108">Tlbimp.exe convertit en une seule opération l’intégralité d’une bibliothèque de types en métadonnées et ne peut pas générer d’informations sur les types pour un sous-ensemble de types définis dans une bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="5b4c9-108">Tlbimp.exe converts an entire type library to metadata at once and cannot generate type information for a subset of the types defined in a type library.</span></span>  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a><span data-ttu-id="5b4c9-109">Pour générer un assembly d’interopérabilité à partir d’une bibliothèque de types</span><span class="sxs-lookup"><span data-stu-id="5b4c9-109">To generate an interop assembly from a type library</span></span>  
  
1. <span data-ttu-id="5b4c9-110">Utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="5b4c9-110">Use the following command:</span></span>  
  
     <span data-ttu-id="5b4c9-111">**Tlbimp**\<*type-library-file*></span><span class="sxs-lookup"><span data-stu-id="5b4c9-111">**tlbimp** \<*type-library-file*></span></span>  
  
     <span data-ttu-id="5b4c9-112">L’ajout du commutateur **/out:** produit un assembly d’interopérabilité avec un nom modifié (LOANLib.dll, par exemple).</span><span class="sxs-lookup"><span data-stu-id="5b4c9-112">Adding the **/out:** switch produces an interop assembly with an altered name, such as LOANLib.dll.</span></span> <span data-ttu-id="5b4c9-113">La modification du nom de l’assembly d’interopérabilité peut aider à le distinguer de la DLL COM d’origine et évite les problèmes qui peuvent survenir quand des noms sont dupliqués.</span><span class="sxs-lookup"><span data-stu-id="5b4c9-113">Altering the interop assembly name can help distinguish it from the original COM DLL and prevent problems that can occur from having duplicate names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b4c9-114"> Exemple</span><span class="sxs-lookup"><span data-stu-id="5b4c9-114">Example</span></span>  

 <span data-ttu-id="5b4c9-115">La commande suivante produit l’assembly Loanlib.dll dans l’espace de noms `Loanlib`.</span><span class="sxs-lookup"><span data-stu-id="5b4c9-115">The following command produces the Loanlib.dll assembly in the `Loanlib` namespace.</span></span>  
  
```console  
tlbimp Loanlib.tlb  
```  
  
 <span data-ttu-id="5b4c9-116">La commande suivante produit un assembly d’interopérabilité avec un nom modifié (LOANLib.dll).</span><span class="sxs-lookup"><span data-stu-id="5b4c9-116">The following command produces an interop assembly with an altered name (LOANLib.dll).</span></span>  
  
```console  
tlbimp LoanLib.tlb /out: LOANLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="5b4c9-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b4c9-117">See also</span></span>

- [<span data-ttu-id="5b4c9-118">Importation d'une bibliothèque de types sous la forme d'un assembly</span><span class="sxs-lookup"><span data-stu-id="5b4c9-118">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="5b4c9-119">Exposition de composants COM au .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5b4c9-119">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
