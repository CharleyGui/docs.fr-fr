---
title: 'Comment : créer une documentation XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: 1421cc85beba42b3cf3656c34b1d02347fbaf164
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403237"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>Comment : créer une documentation XML en Visual Basic

Cet exemple montre comment ajouter des commentaires de documentation XML à votre code.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-xml-documentation-for-a-type-or-member"></a>Pour créer une documentation XML pour un type ou un membre

1. Dans l' **éditeur de code**, placez votre curseur sur la ligne au-dessus du type ou du membre pour lequel vous souhaitez créer la documentation.

2. Type `'''` (trois guillemets simples).

    Un squelette XML pour le type ou le membre est ajouté dans l' **éditeur de code**.

3. Ajoutez des informations descriptives entre les balises appropriées.

    > [!NOTE]
    > Si vous ajoutez des lignes supplémentaires dans le bloc de documentation XML, chaque ligne doit commencer par `'''` .

4. Ajoutez du code supplémentaire qui utilise le type ou le membre avec les nouveaux commentaires de documentation XML.

    IntelliSense affiche le texte de la \<summary> balise pour le type ou le membre.

5. Compilez le code pour générer un fichier XML contenant les commentaires de documentation. Pour plus d’informations, consultez [-doc](../../reference/command-line-compiler/doc.md).

## <a name="see-also"></a>Voir aussi

- [Documentation de votre code avec le langage XML](documenting-your-code-with-xml.md)
- [Étiquettes XML pour les commentaires](../../language-reference/xmldoc/index.md)
- [-doc](../../reference/command-line-compiler/doc.md)
