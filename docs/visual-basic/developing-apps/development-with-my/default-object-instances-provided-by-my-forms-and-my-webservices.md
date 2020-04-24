---
title: Instances d’objets par défaut fournies par My.Forms et My.WebServices
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: d06df4bd023892429b2aaefdd624398a6546d06d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330207"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a><span data-ttu-id="24245-102">Instances d'objets par défaut fournies par My.Forms et My.WebServices (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24245-102">Default Object Instances Provided by My.Forms and My.WebServices (Visual Basic)</span></span>

<span data-ttu-id="24245-103">Les objets [My. Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) et [My. WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) fournissent un accès aux formulaires, aux sources de données et aux services Web XML utilisés par votre application.</span><span class="sxs-lookup"><span data-stu-id="24245-103">The [My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) and [My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) objects provide access to forms, data sources, and XML Web services used by your application.</span></span> <span data-ttu-id="24245-104">Pour ce faire, ils fournissent des collections d' *instances par défaut* de chacun de ces objets.</span><span class="sxs-lookup"><span data-stu-id="24245-104">They do this by providing collections of *default instances* of each of these objects.</span></span>  
  
## <a name="default-instances"></a><span data-ttu-id="24245-105">Instances par défaut</span><span class="sxs-lookup"><span data-stu-id="24245-105">Default Instances</span></span>  

 <span data-ttu-id="24245-106">Une instance par défaut est une instance de la classe fournie par le runtime et n’a pas besoin d’être déclarée et instanciée à `Dim` l' `New` aide des instructions et.</span><span class="sxs-lookup"><span data-stu-id="24245-106">A default instance is an instance of the class that is provided by the runtime and does not need to be declared and instantiated using the `Dim` and `New` statements.</span></span> <span data-ttu-id="24245-107">L’exemple suivant montre comment vous avez pu déclarer et instancier une instance d’une <xref:System.Windows.Forms.Form> classe appelée `Form1`, et comment vous pouvez désormais obtenir une instance par défaut de cette <xref:System.Windows.Forms.Form> classe via. `My.Forms`</span><span class="sxs-lookup"><span data-stu-id="24245-107">The following example demonstrates how you might have declared and instantiated an instance of a <xref:System.Windows.Forms.Form> class called `Form1`, and how you are now able to get a default instance of this <xref:System.Windows.Forms.Form> class through `My.Forms`.</span></span>  
  
 [!code-vb[VbVbcnMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#5)]  
  
 [!code-vb[VbVbcnMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#6)]  
  
 <span data-ttu-id="24245-108">L' `My.Forms` objet retourne une collection d’instances par défaut pour `Form` chaque classe qui existe dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="24245-108">The `My.Forms` object returns a collection of default instances for every `Form` class that exists in your project.</span></span> <span data-ttu-id="24245-109">De même, `My.WebServices` fournit une instance par défaut de la classe proxy pour chaque service Web auquel vous avez créé une référence dans votre application.</span><span class="sxs-lookup"><span data-stu-id="24245-109">Similarly, `My.WebServices` provides a default instance of the proxy class for every Web service that you have created a reference to in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24245-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="24245-110">See also</span></span>

- [<span data-ttu-id="24245-111">My.Forms, objet</span><span class="sxs-lookup"><span data-stu-id="24245-111">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [<span data-ttu-id="24245-112">My.WebServices (objet)</span><span class="sxs-lookup"><span data-stu-id="24245-112">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)
- [<span data-ttu-id="24245-113">Comment My dépend du type de projet</span><span class="sxs-lookup"><span data-stu-id="24245-113">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
