# Present-ViewController-from-CollectionViewCell
Swift 3, CollectionView



// myCollectionViewCell

import UIKit

// 1
protocol myProtocol {
    func loadNewScreen() -> Void;
}

class myCollectionViewCell: BaseCell, UICollectionViewDelegate, UICollectionViewDataSource,UICollectionViewDelegateFlowLayout{
 // 2
   var delegate: myProtocol!

   func collectionView(_ collectionView: UICollectionView, didSelectItemAt indexPath: IndexPath) {
// 3
      delegate?.loadNewScreen()
   }
}


// ViewController

import UIKit

// 4
class ViewController: UIViewController, myProtocol, UICollectionViewDelegate, UICollectionViewDataSource, UICollectionViewDelegateFlowLayout{
    
   @IBOutlet weak var mainCollectionView: UICollectionView!
    
// 5
    func loadNewScreen ()
   {
        let board = UIStoryboard(name: "Main", bundle: nil).instantiateViewController(withIdentifier: "newScreen") as! newController
        present(board, animated: true, completion: nil)
        
   }
// 6
    func collectionView(_ collectionView: UICollectionView, cellForItemAt indexPath: IndexPath) -> UICollectionViewCell {
       cell.delegate = self
   }
    
}
