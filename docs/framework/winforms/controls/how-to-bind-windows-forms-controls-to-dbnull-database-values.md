---
title: 'Procédure : lier des contrôles Windows Forms à des valeurs de base de données DBNull'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingSource component [Windows Forms], binding to DBNull values
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to DBNull values
ms.assetid: 96494e6f-5f40-4f83-af97-bbd7192c2af8
ms.openlocfilehash: 8abce5d69a7cece6528e0c9d8728de0e0acd9305
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591428"
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a>Procédure : lier des contrôles Windows Forms à des valeurs de base de données DBNull
Quand vous liez des contrôles Windows Forms à une source de données et que celle-ci retourne une valeur <xref:System.DBNull>, vous pouvez substituer une valeur appropriée sans gérer, mettre en forme ou analyser des événements. La propriété <xref:System.Windows.Forms.Binding.NullValue%2A> convertira <xref:System.DBNull> en un objet spécifié lors de la mise en forme ou de l'analyse des valeurs de la source de données.  
  
## <a name="example"></a>Exemple  
 Les exemples suivants montrent comment lier une valeur <xref:System.DBNull> dans deux situations différentes. Le premier montre comment définir <xref:System.Windows.Forms.Binding.NullValue%2A> pour une propriété de chaîne ; le second montre comment définir <xref:System.Windows.Forms.Binding.NullValue%2A> pour une propriété d'image.  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 Les types de la propriété liée et de la propriété <xref:System.Windows.Forms.Binding.NullValue%2A> doivent être identiques, sinon une erreur se produit et aucune autre valeur <xref:System.Windows.Forms.Binding.NullValue%2A> n'est traitée. Dans cette situation, aucune exception n'est levée.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- Références aux assemblys System, System.Data, System.Drawing et System.Windows.Forms.  
  
## <a name="see-also"></a>Voir aussi

- [BindingSource, composant](bindingsource-component.md)
- [Guide pratique pour Gérer les erreurs et Exceptions qui se produisent avec Databinding](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
- [Guide pratique pour Lier un contrôle de formulaires Windows à un Type](how-to-bind-a-windows-forms-control-to-a-type.md)
