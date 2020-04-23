---
title: "Comment : générer des assemblys d'interopérabilité à partir de bibliothèques de types"
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- Type Library Importer
- type libraries
- COM interop, importing type library
ms.assetid: 4afd40c3-68f2-41c5-8ec1-4951bc148b9c
ms.openlocfilehash: f4f099dfaf5ff02edd3958d7eab9354ce727a239
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74281804"
---
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a><span data-ttu-id="a4f18-102">Comment : générer des assemblys d'interopérabilité à partir de bibliothèques de types</span><span class="sxs-lookup"><span data-stu-id="a4f18-102">How to: Generate Interop Assemblies from Type Libraries</span></span>
<span data-ttu-id="a4f18-103">L’outil en ligne de commande [Tlbimp.exe (importateur de bibliothèques de types)](../tools/tlbimp-exe-type-library-importer.md) permet de convertir les coclasses et les interfaces figurant dans une bibliothèque de types COM en métadonnées.</span><span class="sxs-lookup"><span data-stu-id="a4f18-103">The [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) is a command-line tool that converts the coclasses and interfaces contained in a COM type library to metadata.</span></span> <span data-ttu-id="a4f18-104">Cet outil crée automatiquement un assembly d’interopérabilité et un espace de noms pour les informations sur les types.</span><span class="sxs-lookup"><span data-stu-id="a4f18-104">This tool creates an interop assembly and namespace for the type information automatically.</span></span> <span data-ttu-id="a4f18-105">Une fois les métadonnées d’une classe disponibles, les clients managés peuvent créer des instances du type COM et appeler ses méthodes, comme s’il s’agissait d’une instance .NET.</span><span class="sxs-lookup"><span data-stu-id="a4f18-105">After the metadata of a class is available, managed clients can create instances of the COM type and call its methods, just as if it were a .NET instance.</span></span> <span data-ttu-id="a4f18-106">Tlbimp.exe convertit en une seule opération l’intégralité d’une bibliothèque de types en métadonnées et ne peut pas générer d’informations sur les types pour un sous-ensemble de types définis dans une bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="a4f18-106">Tlbimp.exe converts an entire type library to metadata at once and cannot generate type information for a subset of the types defined in a type library.</span></span>  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a><span data-ttu-id="a4f18-107">Pour générer un assembly d’interopérabilité à partir d’une bibliothèque de types</span><span class="sxs-lookup"><span data-stu-id="a4f18-107">To generate an interop assembly from a type library</span></span>  
  
1. <span data-ttu-id="a4f18-108">Utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="a4f18-108">Use the following command:</span></span>  
  
     <span data-ttu-id="a4f18-109">**tlbimp** \<*fichier-bibliothèque-types*></span><span class="sxs-lookup"><span data-stu-id="a4f18-109">**tlbimp** \<*type-library-file*></span></span>  
  
     <span data-ttu-id="a4f18-110">L’ajout du commutateur **/out:** produit un assembly d’interopérabilité avec un nom modifié (LOANLib.dll, par exemple).</span><span class="sxs-lookup"><span data-stu-id="a4f18-110">Adding the **/out:** switch produces an interop assembly with an altered name, such as LOANLib.dll.</span></span> <span data-ttu-id="a4f18-111">La modification du nom de l’assembly d’interopérabilité peut aider à le distinguer de la DLL COM d’origine et évite les problèmes qui peuvent survenir quand des noms sont dupliqués.</span><span class="sxs-lookup"><span data-stu-id="a4f18-111">Altering the interop assembly name can help distinguish it from the original COM DLL and prevent problems that can occur from having duplicate names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4f18-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="a4f18-112">Example</span></span>  
 <span data-ttu-id="a4f18-113">La commande suivante produit l’assembly Loanlib.dll dans l’espace de noms `Loanlib`.</span><span class="sxs-lookup"><span data-stu-id="a4f18-113">The following command produces the Loanlib.dll assembly in the `Loanlib` namespace.</span></span>  
  
```console  
tlbimp Loanlib.tlb  
```  
  
 <span data-ttu-id="a4f18-114">La commande suivante produit un assembly d’interopérabilité avec un nom modifié (LOANLib.dll).</span><span class="sxs-lookup"><span data-stu-id="a4f18-114">The following command produces an interop assembly with an altered name (LOANLib.dll).</span></span>  
  
```console  
tlbimp LoanLib.tlb /out: LOANLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="a4f18-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4f18-115">See also</span></span>

- [<span data-ttu-id="a4f18-116">Importation d'une bibliothèque de types sous la forme d'un assembly</span><span class="sxs-lookup"><span data-stu-id="a4f18-116">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="a4f18-117">Exposition de composants COM au .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a4f18-117">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
