# Facial-Expression-Recognition

ექსპერიმენტის ლოგები: 
https://wandb.ai/arevadzemate-free-university-of-tbilisi-/fer2013?nw=nwuserarevadzemate

პირობის წაკითხვისას ნათელი იყო, რომ ამ ამოცანის ამოსახსნელად ყველაზე ეფექტური Convolutional Neural Network ის გამოყენება იქნებოდა. 
მაგრამ გადავწყვიტე, რომ Fully Connected Neural Network ით დამეწყო დატრენინგება, რომ მეჩვენებინა როგორი არაეფექტურია. 

v0: FCNN. არანაირი პრეპროცესინგი, Dropout და Batch normalization-ის გარეშე.

v1: სუსტი CNN. ისევ არანაირი პრეპროცესინგი, Dropout და Batch Norm ის გარეშე. 

v2: CNN 3 დამალული კონვოლუციური ლეიერით. ისევ არანაირი პრეპროცესინგი და არც რეგულარიზაცია

v3: იგივე CNN რაც V2-ში, მაგრამ სტანდარტიზებული დატასეტით.

v4: იგივე CNN ისევ, მაგრამ დატა აუგმენტაციის იმპლემენტაციით, ამ მოდელმა აჩვენა ბევრად ცუდი შედეგი ვიდრე მეგონა აჩვენებდა:

დატა აუგმენტაცია მოიცავდა, რომ სურათების ნაწილი შემეცვალა, ზოგი უფრო მიმეზუმებინა, ზოგში სახე არ ყოფილიყო გაცენტრილი, ზოგი გადამეხარა და ა.შ.
მიზანი ის იყო, რომ ბევრნაირ პორტრეტზე შეძლებოდა ემოციების წაკითხვა. თუმცა ამან არ იმუშავა და რამდენიმე ვარაუდი მაქვს რატომ:

1) ამ პროცესის იმპლემენტაცია Tensorflow ში უფრო ეფექტურია, რადგანაც pytorch-ს ვიყენებ, მომიწია არასტანდარტული გზის გამოყენება.

2) არ მქონდა საკმარისი ეპოქების რაოდენობა

3) ვცადე ერთდროულად ბევრი ტექნიკა აუგმენტაციის

v5: განსხვავებული CNN ბეჩ ნორმალიზაციითა და დროპაუთით. აჩვენა შედარებით უფრო უარესი შედეგი, ვიდრე V3-მა:
dropout rate: 0.5, learning rate: 0.001. 

v6: იგივე მოდელი რაც v5, მაგრამ dropout rate გავხადე 0.3, ხოლო learning rate ვაქციე 0.003. ეს იყო საუკეთესო მოდელი რაც დავატრენინგე.  
   validation accuracy: 57 პროცენტი

v7: ისევ იგივე მოდელი, დატა აუგმენტაციით. ვცადე უფრო ნაკლები ტექნიკა გამომეყენებინა, რადგან ძალიან სახეცვლილ დატასეტზე დატრენინგებას ნორმალურ დატასეტზე ვალიდაციისას კარგი შედეგი არ მოჰქონდა. თუმცა, კიდევ უშედეგოდ ჩაიარა ამ მცდელობამ: (validation accuracy მივიღე 53 პროცენტი)
