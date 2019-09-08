---
title: 'Procédure : Valider des fichiers de mappage externes et DBML'
ms.date: 03/30/2017
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
ms.openlocfilehash: b5901705ac7c0692025ff1f4a4b78f976d62176d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793037"
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a><span data-ttu-id="eac36-102">Procédure : Valider des fichiers de mappage externes et DBML</span><span class="sxs-lookup"><span data-stu-id="eac36-102">How to: Validate DBML and External Mapping Files</span></span>

<span data-ttu-id="eac36-103">Les fichiers de mappage externes et les fichiers .dbml que vous modifiez doivent être validés par rapport à leurs définitions de schéma respectives.</span><span class="sxs-lookup"><span data-stu-id="eac36-103">External mapping files and .dbml files that you modify must be validated against their respective schema definitions.</span></span> <span data-ttu-id="eac36-104">Cette rubrique fournit aux utilisateurs de Visual Studio les étapes nécessaires pour implémenter le processus de validation.</span><span class="sxs-lookup"><span data-stu-id="eac36-104">This topic provides Visual Studio users with the steps to implement the validation process.</span></span>

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

### <a name="to-validate-a-dbml-or-xml-file"></a><span data-ttu-id="eac36-105">Pour valider un fichier .dbml ou XML</span><span class="sxs-lookup"><span data-stu-id="eac36-105">To validate a .dbml or XML file</span></span>

1. <span data-ttu-id="eac36-106">Dans le menu **fichier** de Visual Studio, pointez sur **ouvrir**, puis cliquez sur **fichier**.</span><span class="sxs-lookup"><span data-stu-id="eac36-106">On the Visual Studio **File** menu, point to **Open**, and then click **File**.</span></span>

2. <span data-ttu-id="eac36-107">Dans la boîte de dialogue **ouvrir un fichier** , cliquez sur le fichier de mappage. dbml ou XML que vous souhaitez valider.</span><span class="sxs-lookup"><span data-stu-id="eac36-107">In the **Open File** dialog box, click the .dbml or XML mapping file that you want to validate.</span></span>

    <span data-ttu-id="eac36-108">Le fichier s’ouvre dans l' **éditeur XML**.</span><span class="sxs-lookup"><span data-stu-id="eac36-108">The file opens in the **XML Editor**.</span></span>

3. <span data-ttu-id="eac36-109">Cliquez avec le bouton droit sur la fenêtre, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="eac36-109">Right-click the window, and then click **Properties**.</span></span>

4. <span data-ttu-id="eac36-110">Dans la fenêtre **Propriétés** , cliquez sur le bouton de sélection de la propriété **schémas** .</span><span class="sxs-lookup"><span data-stu-id="eac36-110">In the **Properties** window, click the ellipsis for the **Schemas** property.</span></span>

    <span data-ttu-id="eac36-111">La boîte de dialogue **schémas XML** s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="eac36-111">The **XML Schemas** dialog box opens.</span></span>

5. <span data-ttu-id="eac36-112">Notez la définition de schéma en fonction de vos besoins.</span><span class="sxs-lookup"><span data-stu-id="eac36-112">Note the appropriate schema definition for your purpose.</span></span>

    - <span data-ttu-id="eac36-113">DbmlSchema.xsd est la définition de schéma pour valider un fichier .dbml.</span><span class="sxs-lookup"><span data-stu-id="eac36-113">DbmlSchema.xsd is the schema definition for validating a .dbml file.</span></span> <span data-ttu-id="eac36-114">Pour plus d’informations, consultez [génération de code dans LINQ to SQL](code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="eac36-114">For more information, see [Code Generation in LINQ to SQL](code-generation-in-linq-to-sql.md).</span></span>

    - <span data-ttu-id="eac36-115">LinqToSqlMapping.xsd est la définition de schéma pour valider un fichier mappage XML externe.</span><span class="sxs-lookup"><span data-stu-id="eac36-115">LinqToSqlMapping.xsd is the schema definition for validating an external XML mapping file.</span></span> <span data-ttu-id="eac36-116">Pour plus d’informations, consultez [mappage externe](external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="eac36-116">For more information, see [External Mapping](external-mapping.md).</span></span>

6. <span data-ttu-id="eac36-117">Dans la colonne **use** de la ligne de définition de schéma souhaitée, cliquez pour ouvrir la zone de liste déroulante, puis cliquez sur **use this Schema**.</span><span class="sxs-lookup"><span data-stu-id="eac36-117">In the **Use** column of the desired schema definition row, click to open the drop-down box, and then click **Use this schema**.</span></span>

    <span data-ttu-id="eac36-118">Le fichier de définition de schéma est maintenant associé à votre fichier DBML ou votre fichier mappage XML.</span><span class="sxs-lookup"><span data-stu-id="eac36-118">The schema definition file is now associated with your DBML or XML mapping file.</span></span>

    <span data-ttu-id="eac36-119">Assurez-vous qu'aucune autre définition de schéma n'est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="eac36-119">Make sure no other schema definitions are selected.</span></span>

7. <span data-ttu-id="eac36-120">Dans le menu **affichage** , cliquez sur **liste d’erreurs**.</span><span class="sxs-lookup"><span data-stu-id="eac36-120">On the **View** menu, click **Error List**.</span></span>

    <span data-ttu-id="eac36-121">Déterminez si des erreurs, avertissements ou messages ont été générés.</span><span class="sxs-lookup"><span data-stu-id="eac36-121">Determine whether errors, warnings, or messages have been generated.</span></span> <span data-ttu-id="eac36-122">Si ce n'est pas le cas, le fichier XML est valide par rapport à la définition de schéma.</span><span class="sxs-lookup"><span data-stu-id="eac36-122">If not, the XML file is valid against the schema definition.</span></span>

## <a name="alternate-method-for-supplying-schema-definition"></a><span data-ttu-id="eac36-123">Méthode alternative pour fournir la définition de schéma</span><span class="sxs-lookup"><span data-stu-id="eac36-123">Alternate Method for Supplying Schema Definition</span></span>

<span data-ttu-id="eac36-124">Si, pour une raison quelconque, le fichier. xsd approprié n’apparaît pas dans la boîte de dialogue **schémas XML** , vous pouvez télécharger le fichier. xsd à partir d’une rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="eac36-124">If for some reason the appropriate .xsd file does not appear in the **XML Schemas** dialog box, you can download the .xsd file from a Help topic.</span></span> <span data-ttu-id="eac36-125">Les étapes suivantes vous permettent d’enregistrer le fichier téléchargé au format Unicode requis par l’éditeur XML de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="eac36-125">The following steps help you save the downloaded file in the Unicode format required by the Visual Studio XML Editor.</span></span>

#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a><span data-ttu-id="eac36-126">Pour copier un fichier de définition de schéma à partir d'une rubrique d'aide</span><span class="sxs-lookup"><span data-stu-id="eac36-126">To copy a schema definition file from a Help topic</span></span>

1. <span data-ttu-id="eac36-127">Recherchez la rubrique d'aide qui contient la définition de schéma comme décrit précédemment dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="eac36-127">Locate the Help topic that contains the schema definition as described earlier in this topic.</span></span>

    - <span data-ttu-id="eac36-128">Pour les fichiers. dbml, consultez [génération de code dans LINQ to SQL](code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="eac36-128">For .dbml files, see [Code Generation in LINQ to SQL](code-generation-in-linq-to-sql.md).</span></span>

    - <span data-ttu-id="eac36-129">Pour les fichiers de mappage externes, consultez [mappage externe](external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="eac36-129">For external mapping files, see [External Mapping](external-mapping.md).</span></span>

2. <span data-ttu-id="eac36-130">Cliquez sur **copier le code** pour copier le fichier de code dans le presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="eac36-130">Click **Copy Code** to copy the code file to the Clipboard.</span></span>

3. <span data-ttu-id="eac36-131">Lancez le Bloc-notes pour créer un nouveau fichier.</span><span class="sxs-lookup"><span data-stu-id="eac36-131">Start Notepad to create a new file.</span></span>

4. <span data-ttu-id="eac36-132">Collez le code du Presse-papiers dans un fichier Bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="eac36-132">Paste the code from the clipboard into Notepad file.</span></span>

5. <span data-ttu-id="eac36-133">Dans le menu **fichier** du bloc-notes, cliquez sur **Enregistrer sous**.</span><span class="sxs-lookup"><span data-stu-id="eac36-133">On the Notepad **File** menu, click **Save As**.</span></span>

6. <span data-ttu-id="eac36-134">Dans la zone **codage** , sélectionnez **Unicode**.</span><span class="sxs-lookup"><span data-stu-id="eac36-134">In the **Encoding** box, select **Unicode**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="eac36-135">Cette sélection garantit que le marqueur d'ordre d'octet Unicode 16 bits (`FFFE`) est ajouté au fichier texte.</span><span class="sxs-lookup"><span data-stu-id="eac36-135">This selection guarantees that the Unicode-16 byte-order marker (`FFFE`) is prepended to the text file.</span></span>

7. <span data-ttu-id="eac36-136">Dans la zone **nom de fichier** , créez un nom de fichier avec une extension. xsd.</span><span class="sxs-lookup"><span data-stu-id="eac36-136">In the **File name** box, create a file name with an .xsd extension.</span></span>

## <a name="see-also"></a><span data-ttu-id="eac36-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eac36-137">See also</span></span>

- [<span data-ttu-id="eac36-138">Référence</span><span class="sxs-lookup"><span data-stu-id="eac36-138">Reference</span></span>](reference.md)
