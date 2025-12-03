Pseudocode for Intelligent Medical Triage System

Function 1: Add Patient to Waiting Line (Heap)

Function EnqueuePatient(patient):
    If heap is full:
        Print "Heap overflow"
    Else:
        Add patient at the end of the heap
        Set i = index of added patient
        While i != 0 and patient priority > parent priority:
            Swap patient with parent
            Set i = parent index


Function 2: Serve Next Patient (Heap)

Function DequeuePatient():
    If heap is empty:
        Print "No patients in queue"
        Return null
    Else:
        Store root patient as servedPatient
        Replace root with last element in heap
        Reduce heap size by 1
        Heapify at root to maintain max-heap
        Return servedPatient


Function 3: Search Patient by ID (Hash Table)

Function SearchPatientByID(ID):
    index = hash(ID) % hashTable size
    node = hashTable[index]
    While node is not null:
        If node.ID == ID:
            Return node.patient
        node = node.next
    Return "Patient not found"


Function 4: Add Patient History (Linked List)

Function AddMedicalHistory(patient):
    Create new node with patient data
    Set new node next = head of linked list
    Set head = new node


Function 5: Insert Patient into AVL Tree

Function InsertAVLTree(patient):
    If tree is empty:
        Create new node with patient
        Return node
    Else:
        If patient.ID < current node.ID:
            node.left = InsertAVLTree(patient) on left subtree
        Else if patient.ID > current node.ID:
            node.right = InsertAVLTree(patient) on right subtree
        Else:
            Return current node (duplicate ID)
    Update height of current node
    balance = height(left subtree) - height(right subtree)
    If balance > 1 and patient.ID < node.left.ID:
        Return RightRotate(node)
    If balance < -1 and patient.ID > node.right.ID:
        Return LeftRotate(node)
    If balance > 1 and patient.ID > node.left.ID:
        node.left = LeftRotate(node.left)
        Return RightRotate(node)
    If balance < -1 and patient.ID < node.right.ID:
        node.right = RightRotate(node.right)
        Return LeftRotate(node)
    Return node
