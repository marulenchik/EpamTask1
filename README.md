# EpamTask1

Step 1: 
Stack:
  String name = "Kevin";
Heap:
  name → H1	H1: String "Kevin" (interned)

Step 2: 
Stack:
  name → H1	
  list → H2	

Heap:
  H1: String "Kevin"
  H2: ArrayList instance { elementData → H3, size = 0 }
  H3: Object[10] (initial capacity 10)

Step 3: 
Stack:
  name → H1	
  list → H2	
  times = 10	

Heap:
  H1: String "Kevin"
  H2: ArrayList { elementData → H3, size = 0 }
  H3: Object[10]

Step 4: call fill(list, name+name, times)
fill:	
Stack:
  collection → H2	
  str → H4	
  times = 10	

Heap:
  H1: "Kevin"
  H2: ArrayList { elementData → H3, size = 0 }
  H3: Object[10]
  H4: String "KevinKevin"

Step 5: call shrink(str)
shrink frame:	
Stack:
  str → H4	
  newLength = 5	
  chars → C5	
  
Heap:
H1: "Kevin"
  H2: ArrayList { elementData → H3, size = 0 }
  H3: Object[10]
  H4: "KevinKevin"
  char[5]{'K','v','n','e','i'}
	H6: String "Kvnei" 

Step 6: 
Stack:
  collection → H2
  str → H4
  times = 7
  shrunk → H6
Heap:
  H1: "Kevin"
  H2: ArrayList { elementData → H3, size = 0 }
  H3: Object[10]
  H4: "KevinKevin"
	C5: char[5]{'K','v','n','e','i'}
	H6: "Kvnei"

Step 7: for (i = 0; i < times/2; i++) collection.add(shrunk);
Stack:
  collection → H2	
  str → H4	
  times = 7	
  shrunk → H6
  i = 3 (loop ended)	
Heap:
  H1: "Kevin"
  H2: ArrayList { elementData → H3, size = 3 }
  H3: Object[10] [ H6, H6, H6, null,… ]
  H4: "KevinKevin"
  C5: char[5]{'K','v','n','e','i'}
	H6: "Kvnei"

Step 8: return from fill
Stack:
  name → H1	
  list → H2	
  times = 10	
Heap:
  H1: "Kevin"
  H2: ArrayList { elementData → H3, size = 3 }
  H3: Object[10] [ H6, H6, H6, null,… ]
  H4: "KevinKevin"
	C5: char[5]{'K','v','n','e','i'}
	H6: "Kvnei"

Step 9: compute times + 7 = 17, call println

The end.
