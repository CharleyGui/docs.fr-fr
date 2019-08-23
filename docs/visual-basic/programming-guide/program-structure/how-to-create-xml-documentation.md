---
title: 'Procédure : Créer une documentation XML dans Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: 9380c23ab6cfdbecd519926229b45ed863f07f9e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947717"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>Procédure : Créer une documentation XML dans Visual Basic
Cet exemple montre comment ajouter des commentaires de documentation XML à votre code.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a>Pour créer une documentation XML pour un type ou un membre  
  
1. Dans l' **éditeur de code**, placez votre curseur sur la ligne au-dessus du type ou du membre pour lequel vous souhaitez créer la documentation.  
  
2. Type `'''` (trois guillemets simples).  
  
     Un squelette XML pour le type ou le membre est ajouté dans l' **éditeur de code**.  
  
3. Ajoutez des informations descriptives entre les balises appropriées.  
  
    > [!NOTE]
    > Si vous ajoutez des lignes supplémentaires dans le bloc de documentation XML, chaque ligne doit `'''`commencer par.  
  
4. Ajoutez du code supplémentaire qui utilise le type ou le membre avec les nouveaux commentaires de documentation XML.  
  
     IntelliSense affiche le texte de la \<balise de synthèse > pour le type ou le membre.  
  
5. Compilez le code pour générer un fichier XML contenant les commentaires de documentation. Pour plus d’informations, consultez [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).  
  
## <a name="see-also"></a>Voir aussi

- [Documentation de votre code avec le langage XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [Étiquettes XML pour les commentaires](../../../visual-basic/language-reference/xmldoc/index.md)
- [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
