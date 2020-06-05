---
title: Numéro d'enregistrement incorrect
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: 44a11d95d33041de9d637684f41cb003dcc36b97
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84367540"
---
# <a name="bad-record-number"></a><span data-ttu-id="aca74-102">Numéro d'enregistrement incorrect</span><span class="sxs-lookup"><span data-stu-id="aca74-102">Bad record number</span></span>
<span data-ttu-id="aca74-103">Le numéro d’enregistrement dans une instruction `a FileGet`, `FilePut`, `FileGetObject`ou `FilePutObject` est inférieur ou égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="aca74-103">The record number in `a FileGet`, `FilePut`, `FileGetObject`, or `FilePutObject` statement is less than or equal to zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="aca74-104">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="aca74-104">To correct this error</span></span>  
  
1. <span data-ttu-id="aca74-105">Vérifiez les calculs utilisés pour générer le numéro d’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="aca74-105">Check the calculations used in generating the record number.</span></span> <span data-ttu-id="aca74-106">Vérifiez l’orthographe des variables contenant le numéro d’enregistrement ou utilisées dans le calcul des numéros d’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="aca74-106">Verify spelling of the variables containing the record number or used in calculating record numbers.</span></span> <span data-ttu-id="aca74-107">Un nom de variable mal orthographié est déclaré implicitement et possède une valeur égale à zéro, sauf si vous avez utilisé `Option Explicit On` dans le module.</span><span class="sxs-lookup"><span data-stu-id="aca74-107">A misspelled variable name is implicitly declared and initialized to zero, unless you used `Option Explicit On` in the module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aca74-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aca74-108">See also</span></span>

- [<span data-ttu-id="aca74-109">Option Explicit (instruction)</span><span class="sxs-lookup"><span data-stu-id="aca74-109">Option Explicit Statement</span></span>](../language-reference/statements/option-explicit-statement.md)
