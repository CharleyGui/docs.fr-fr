---
title: 'Procédure : Valider des fichiers de mappage externes et DBML'
ms.date: 03/30/2017
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
ms.openlocfilehash: 212d65dfe998b825dd40e564756083ed685dff6f
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041143"
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a>Procédure : Valider des fichiers de mappage externes et DBML

Les fichiers de mappage externes et les fichiers .dbml que vous modifiez doivent être validés par rapport à leurs définitions de schéma respectives. Cette rubrique fournit aux utilisateurs de Visual Studio les étapes nécessaires pour implémenter le processus de validation.

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

### <a name="to-validate-a-dbml-or-xml-file"></a>Pour valider un fichier .dbml ou XML

1. Dans le menu **fichier** de Visual Studio, pointez sur **ouvrir**, puis cliquez sur **fichier**.

2. Dans la boîte de dialogue **ouvrir un fichier** , cliquez sur le fichier de mappage. dbml ou XML que vous souhaitez valider.

    Le fichier s’ouvre dans l' **éditeur XML**.

3. Cliquez avec le bouton droit sur la fenêtre, puis cliquez sur **Propriétés**.

4. Dans la fenêtre **Propriétés** , cliquez sur le bouton de sélection de la propriété **schémas** .

    La boîte de dialogue **schémas XML** s’ouvre.

5. Notez la définition de schéma en fonction de vos besoins.

    - DbmlSchema.xsd est la définition de schéma pour valider un fichier .dbml. Pour plus d’informations, consultez [génération de code dans LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).

    - LinqToSqlMapping.xsd est la définition de schéma pour valider un fichier mappage XML externe. Pour plus d’informations, consultez [mappage externe](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).

6. Dans la colonne **use** de la ligne de définition de schéma souhaitée, cliquez pour ouvrir la zone de liste déroulante, puis cliquez sur **use this Schema**.

    Le fichier de définition de schéma est maintenant associé à votre fichier DBML ou votre fichier mappage XML.

    Assurez-vous qu'aucune autre définition de schéma n'est sélectionnée.

7. Dans le menu **affichage** , cliquez sur **liste d’erreurs**.

    Déterminez si des erreurs, avertissements ou messages ont été générés. Si ce n'est pas le cas, le fichier XML est valide par rapport à la définition de schéma.

## <a name="alternate-method-for-supplying-schema-definition"></a>Méthode alternative pour fournir la définition de schéma

Si, pour une raison quelconque, le fichier. xsd approprié n’apparaît pas dans la boîte de dialogue **schémas XML** , vous pouvez télécharger le fichier. xsd à partir d’une rubrique d’aide. Les étapes suivantes vous permettent d’enregistrer le fichier téléchargé au format Unicode requis par l’éditeur XML de Visual Studio.

#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a>Pour copier un fichier de définition de schéma à partir d'une rubrique d'aide

1. Recherchez la rubrique d'aide qui contient la définition de schéma comme décrit précédemment dans cette rubrique.

    - Pour les fichiers. dbml, consultez [génération de code dans LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).

    - Pour les fichiers de mappage externes, consultez [mappage externe](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).

2. Cliquez sur **copier le code** pour copier le fichier de code dans le presse-papiers.

3. Lancez le Bloc-notes pour créer un nouveau fichier.

4. Collez le code du Presse-papiers dans un fichier Bloc-notes.

5. Dans le menu **fichier** du bloc-notes, cliquez sur **Enregistrer sous**.

6. Dans la zone **codage** , sélectionnez **Unicode**.

    > [!IMPORTANT]
    > Cette sélection garantit que le marqueur d'ordre d'octet Unicode 16 bits (`FFFE`) est ajouté au fichier texte.

7. Dans la zone **nom de fichier** , créez un nom de fichier avec une extension. xsd.

## <a name="see-also"></a>Voir aussi

- [Référence](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
