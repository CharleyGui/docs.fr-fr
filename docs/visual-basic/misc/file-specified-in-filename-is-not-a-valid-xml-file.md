---
title: Le fichier spécifié dans FileName n’est pas un fichier XML valide
ms.date: 07/20/2015
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
ms.openlocfilehash: 7d9500e58044f52a4e2508c9cb23a0e8186bc08d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553894"
---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a><span data-ttu-id="85f11-102">Le fichier spécifié dans FileName n’est pas un fichier XML valide</span><span class="sxs-lookup"><span data-stu-id="85f11-102">File specified in FileName is not a valid XML file</span></span>

<span data-ttu-id="85f11-103">Le nom de fichier fourni n’est pas un fichier XML valide.</span><span class="sxs-lookup"><span data-stu-id="85f11-103">The file name that you supplied is not a valid XML file.</span></span> <span data-ttu-id="85f11-104">Pour spécifier la structure et le contenu autorisés d’un document XML, vous pouvez utiliser une définition de type de document (DTD), un schéma Microsoft XML-Data Reduced (XDR) ou un schéma de langage de définition de schéma XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="85f11-104">To specify the allowed structure and content of an XML document, you can use a Document Type Definition (DTD), a Microsoft XML-Data Reduced (XDR) schema, or an XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="85f11-105">Les schémas XSD constituent la meilleure façon de spécifier des grammaires XML dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="85f11-105">XSD schemas are the preferred way to specify XML grammars in the .NET Framework.</span></span>

> [!NOTE]
> <span data-ttu-id="85f11-106">Dans certaines versions antérieures de Visual Studio, le **Concepteur XML** est le concepteur pour le schéma XML et les datasets typés.</span><span class="sxs-lookup"><span data-stu-id="85f11-106">In some earlier versions of Visual Studio, the **XML Designer** is the designer for typed datasets and XML schema.</span></span> <span data-ttu-id="85f11-107">Vous pouvez toujours utiliser le **Concepteur XML** pour créer et modifier des fichiers de schéma XML.</span><span class="sxs-lookup"><span data-stu-id="85f11-107">The **XML Designer** can still be used to create and edit XML schema files.</span></span> <span data-ttu-id="85f11-108">Toutefois, dans Visual Studio 2012, le concepteur pour la création et la modification de datasets typés est le **Concepteur de DataSet**.</span><span class="sxs-lookup"><span data-stu-id="85f11-108">However, in Visual Studio 2012, the designer for creating and editing typed datasets is the **Dataset Designer**.</span></span> <span data-ttu-id="85f11-109">Pour plus d’informations, consultez [création et modification de datasets typés](/previous-versions/visualstudio/visual-studio-2013/314t4see(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="85f11-109">For more information, see [Creating and Editing Typed Datasets](/previous-versions/visualstudio/visual-studio-2013/314t4see(v=vs.120)).</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="85f11-110">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="85f11-110">To correct this error</span></span>

- <span data-ttu-id="85f11-111">Vérifiez que le nom du fichier que vous fournissez est correct.</span><span class="sxs-lookup"><span data-stu-id="85f11-111">Check that you are supplying the correct file name.</span></span>

- <span data-ttu-id="85f11-112">Vérifiez que le fichier spécifié contient le code XML valide. Pour cela, chargez le fichier XML à vérifier dans le **Concepteur XML**.</span><span class="sxs-lookup"><span data-stu-id="85f11-112">Check that the specified file contains valid XML by loading the XML file that you want to check into the **XML Designer**.</span></span> <span data-ttu-id="85f11-113">Dans le menu **XML** , cliquez sur **Valider le XML**.</span><span class="sxs-lookup"><span data-stu-id="85f11-113">From the **XML** menu, click **Validate XML**.</span></span> <span data-ttu-id="85f11-114">Les erreurs sont répertoriées dans la **Liste des tâches**.</span><span class="sxs-lookup"><span data-stu-id="85f11-114">Errors are displayed in the **Task List**.</span></span>

- <span data-ttu-id="85f11-115">Si le fichier XML comprend un schéma XML associé, vérifiez que les éléments apparaissent dans la structure définie et que le contenu de chaque élément est conforme aux types de données déclarés qui sont spécifiés dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="85f11-115">If the XML file has an associated XML Schema, check that the elements appear in the defined structure and that the content of the individual elements conforms to the declared data types specified in the schema.</span></span>

## <a name="see-also"></a><span data-ttu-id="85f11-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85f11-116">See also</span></span>

- <xref:System.Xml>
- [<span data-ttu-id="85f11-117">Procédure : analyser des chemins de fichiers</span><span class="sxs-lookup"><span data-stu-id="85f11-117">How to: Parse File Paths</span></span>](../developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
