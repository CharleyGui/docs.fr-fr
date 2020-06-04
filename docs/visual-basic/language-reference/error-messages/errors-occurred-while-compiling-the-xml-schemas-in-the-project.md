---
title: Des erreurs se sont produites lors de la compilation des schémas Xml du projet
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 919c6873ba63addb776d756a58c44a3fe3f0ec3d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409624"
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a><span data-ttu-id="5683b-102">Des erreurs se sont produites lors de la compilation des schémas Xml du projet</span><span class="sxs-lookup"><span data-stu-id="5683b-102">Errors occurred while compiling the XML schemas in the project</span></span>
<span data-ttu-id="5683b-103">Des erreurs se sont produites lors de la compilation des schémas XML dans le projet.</span><span class="sxs-lookup"><span data-stu-id="5683b-103">Errors occurred while compiling the XML schemas in the project.</span></span> <span data-ttu-id="5683b-104">Pour cette raison, XML IntelliSense n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="5683b-104">Because of this, XML IntelliSense is not available.</span></span>  
  
 <span data-ttu-id="5683b-105">Il y a une erreur dans un schéma XSD (XML Schema Definition) inclus dans le projet.</span><span class="sxs-lookup"><span data-stu-id="5683b-105">There is an error in an XML Schema Definition (XSD) schema included in the project.</span></span> <span data-ttu-id="5683b-106">Cette erreur se produit lorsque vous ajoutez un fichier de schéma XSD (. xsd) qui est en conflit avec le jeu de schémas XSD existant pour le projet.</span><span class="sxs-lookup"><span data-stu-id="5683b-106">This error occurs when you add an XSD schema (.xsd) file that conflicts with the existing XSD schema set for the project.</span></span>  
  
 <span data-ttu-id="5683b-107">**ID d’erreur :** BC36810</span><span class="sxs-lookup"><span data-stu-id="5683b-107">**Error ID:** BC36810</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5683b-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="5683b-108">To correct this error</span></span>  
  
- <span data-ttu-id="5683b-109">Double-cliquez sur l’avertissement dans la fenêtre **liste d’erreurs** .</span><span class="sxs-lookup"><span data-stu-id="5683b-109">Double-click the warning in the **Errors List** window.</span></span> <span data-ttu-id="5683b-110">Visual Basic vous reconnectera à l’emplacement dans le fichier XSD qui est la source de l’avertissement.</span><span class="sxs-lookup"><span data-stu-id="5683b-110">Visual Basic will take you to the location in the XSD file that is the source of the warning.</span></span> <span data-ttu-id="5683b-111">Corrigez l’erreur dans le schéma XSD.</span><span class="sxs-lookup"><span data-stu-id="5683b-111">Correct the error in the XSD schema.</span></span>  
  
- <span data-ttu-id="5683b-112">Assurez-vous que tous les fichiers de schéma XSD (. xsd) requis sont inclus dans le projet.</span><span class="sxs-lookup"><span data-stu-id="5683b-112">Ensure that all required XSD schema (.xsd) files are included in the project.</span></span> <span data-ttu-id="5683b-113">Vous devrez peut-être cliquer sur **Afficher tous les fichiers** dans le menu **projet** pour afficher vos fichiers. xsd dans **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="5683b-113">You may need to click **Show All Files** on the **Project** menu to see your .xsd files in **Solution Explorer**.</span></span> <span data-ttu-id="5683b-114">Cliquez avec le bouton droit sur un fichier. xsd, puis cliquez sur **inclure dans le projet** pour inclure le fichier dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="5683b-114">Right-click an .xsd file and then click **Include In Project** to include the file in your project.</span></span>  
  
- <span data-ttu-id="5683b-115">Si vous utilisez l’Assistant XML vers schéma, cette erreur peut se produire si vous déduisez des schémas plus d’une fois à partir de la même source.</span><span class="sxs-lookup"><span data-stu-id="5683b-115">If you are using the XML to Schema Wizard, this error can occur if you infer schemas more than one time from the same source.</span></span> <span data-ttu-id="5683b-116">Dans ce cas, vous pouvez supprimer les fichiers de schéma XSD existants du projet, ajouter un nouveau modèle d’élément de schéma XML à, puis fournir l’Assistant XML au schéma avec toutes les sources XML applicables à votre projet.</span><span class="sxs-lookup"><span data-stu-id="5683b-116">In this case, you can remove the existing XSD schema files from the project, add a new XML to Schema item template, and then provide the XML to Schema Wizard with all the applicable XML sources for your project.</span></span>  
  
- <span data-ttu-id="5683b-117">Si aucune erreur n’est identifiée dans votre schéma XSD, le compilateur XML peut ne pas disposer d’informations suffisantes pour fournir un message d’erreur détaillé.</span><span class="sxs-lookup"><span data-stu-id="5683b-117">If no error is identified in your XSD schema, the XML compiler may not have enough information to provide a detailed error message.</span></span> <span data-ttu-id="5683b-118">Vous pourrez peut-être obtenir des informations d’erreur plus détaillées si vous vous assurez que les espaces de noms XML des fichiers. xsd inclus dans votre projet correspondent aux espaces de noms XML identifiés pour le jeu de schémas XML dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5683b-118">You may be able to get more detailed error information if you ensure that the XML namespaces for the .xsd files included in your project match the XML namespaces identified for the XML Schema set in Visual Studio.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5683b-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5683b-119">See also</span></span>

- [<span data-ttu-id="5683b-120">Fenêtre Liste d’erreurs</span><span class="sxs-lookup"><span data-stu-id="5683b-120">Error List Window</span></span>](/visualstudio/ide/reference/error-list-window)
- [<span data-ttu-id="5683b-121">XML</span><span class="sxs-lookup"><span data-stu-id="5683b-121">XML</span></span>](../../programming-guide/language-features/xml/index.md)
