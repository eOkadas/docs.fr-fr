---
title: 'Procédure : Définir des images au moment de l’exécution (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- pictures [Windows Forms], setting display
- examples [Windows Forms], PictureBox control
- bitmaps [Windows Forms], displaying in PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding images
- images [Windows Forms], adding with PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 18ca41d0-68a5-4660-985e-a6c1fbc01d76
ms.openlocfilehash: 99d78a275c8ad8f55d9b0832a794545b65da7e20
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917525"
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a>Procédure : Définir des images au moment de l’exécution (Windows Forms)
Vous pouvez définir par programmation l’image affichée par un contrôle Windows Forms <xref:System.Windows.Forms.PictureBox> .  
  
### <a name="to-set-a-picture-programmatically"></a>Pour définir une image par programmation  
  
- Définissez la <xref:System.Windows.Forms.PictureBox.Image%2A> propriété à l' <xref:System.Drawing.Image.FromFile%2A> aide de la <xref:System.Drawing.Image> méthode de la classe.  
  
     Dans l’exemple ci-dessous, le chemin d’accès défini pour l’emplacement de l’image est le dossier Mes documents. En effet, vous pouvez supposer que la plupart des ordinateurs exécutant le système d’exploitation Windows incluent ce répertoire. Cela permet également aux utilisateurs avec des niveaux d’accès minimum au système d’exécuter l’application en toute sécurité. L’exemple ci-dessous suppose qu’un formulaire <xref:System.Windows.Forms.PictureBox> avec un contrôle a déjà été ajouté.  
  
    ```vb  
    Private Sub LoadNewPict()  
       ' You should replace the bold image   
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
    ```  
  
    ```csharp  
    private void LoadNewPict(){  
       // You should replace the bold image   
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
    }  
    ```  
  
    ```cpp  
    private:  
       void LoadNewPict()  
       {  
          // You should replace the bold image   
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
### <a name="to-clear-a-graphic"></a>Pour effacer un graphique  
  
- Tout d’abord, libérez la mémoire utilisée par l’image, puis effacez le graphique. Le garbage collection libérera de la mémoire plus tard si la gestion de la mémoire devient un problème.  
  
    ```vb  
    If Not (PictureBox1.Image Is Nothing) Then  
       PictureBox1.Image.Dispose()  
       PictureBox1.Image = Nothing  
    End If  
    ```  
  
    ```csharp  
    if (pictureBox1.Image != null)   
    {  
       pictureBox1.Image.Dispose();  
       pictureBox1.Image = null;  
    }  
    ```  
  
    ```cpp  
    if (pictureBox1->Image != nullptr)  
    {  
       pictureBox1->Image->Dispose();  
       pictureBox1->Image = nullptr;  
    }  
    ```  
  
    > [!NOTE]
    > Pour plus d’informations sur les raisons pour lesquelles <xref:System.Drawing.Image.Dispose%2A> vous devez utiliser la méthode de cette manière, consultez [nettoyage des ressources non managées](../../../standard/garbage-collection/unmanaged.md).  
  
     Ce code efface l’image même si un graphique a été chargé dans le contrôle au moment du Design.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.PictureBox>
- <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>
- [Vue d’ensemble du contrôle PictureBox](picturebox-control-overview-windows-forms.md)
- [Guide pratique pour Charger une image à l’aide du concepteur](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [Guide pratique : Modifier la taille ou l’emplacement d’une image au moment de l’exécution](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [PictureBox, contrôle](picturebox-control-windows-forms.md)
