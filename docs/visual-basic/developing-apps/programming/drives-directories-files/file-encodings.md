---
title: Encodages de fichiers
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: f906b2f2d747a7950c70a24549bbf5423e5b87b4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401743"
---
# <a name="file-encodings-visual-basic"></a>Encodages de fichiers (Visual Basic)

Les encodages de fichiers, également appelés codages de caractères, spécifient comment représenter les caractères lors du traitement du texte. Un encodage peut être préférable à un autre en fonction des caractères de langue qu’il peut ou non gérer, bien qu’Unicode soit généralement privilégié.

Lors de la lecture ou de l’écriture dans des fichiers, des incohérences d’encodage de fichiers peuvent provoquer des exceptions ou des résultats incorrects.

## <a name="types-of-encodings"></a>Types d’encodages

Unicode est l’encodage à utiliser par défaut quand vous travaillez avec des fichiers. Unicode est une norme internationale d’encodage de caractères qui utilise des valeurs de code de 16 bits pour représenter tous les caractères utilisés dans l’informatique moderne, notamment les symboles techniques et les caractères spéciaux utilisés dans l’édition.

Les anciennes normes d’encodage de caractères se composaient de jeux de caractères traditionnels, tels que le jeu de caractères ANSI Windows qui utilise des valeurs de code de 8 bits ou des combinaisons de valeurs de 8 bits, pour représenter les caractères utilisés dans une langue ou une région géographique spécifique.

## <a name="encoding-class"></a>Classe d’encodage

La classe <xref:System.Text.Encoding> représente un encodage de caractères. Ce tableau liste et décrit les types d’encodages disponibles.

|Nom|Description|
|---|---|
|<xref:System.Text.ASCIIEncoding>|Représente un encodage de caractères ASCII de caractères Unicode.|
|<xref:System.Text.UnicodeEncoding>|Représente un encodage UTF-16 de caractères Unicode.|
|<xref:System.Text.UTF32Encoding>|Représente un encodage UTF-32 de caractères Unicode.|
|<xref:System.Text.UTF7Encoding>|Représente un encodage UTF-7 de caractères Unicode.|
|<xref:System.Text.UTF8Encoding>|Représente un encodage UTF-8 de caractères Unicode.|

## <a name="see-also"></a>Voir aussi

- [Lecture à partir de fichiers](reading-from-files.md)
- [Écriture dans des fichiers](writing-to-files.md)
