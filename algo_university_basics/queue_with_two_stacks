def main():
    try:
        file_input = open('input.txt', 'r')
        file_output = open('output.txt', 'w')
    except FileNotFoundError:
        print("can't open")
    new_queue = Queue()
    for line in file_input:
        line = line.split()
        if line[0] == '+':
            new_queue.push(line[1])
        elif line[0] == '?':
            file_output.write(new_queue.min() + '\n')
        else:
            file_output.write(new_queue.pop() + '\n')


class Stack:
    def __init__(self):
        self.stack = []
        self.min_element = None

    def push(self, element):
        if self.min_element is None:
            self.min_element = element
        elif element < self.min_element:
            self.min_element = element
        temp = (element, self.min_element)
        self.stack.append(temp)

    def pop(self):
        temp = self.stack[len(self.stack) - 1][0]
        self.stack.pop()
        return temp

    def peek(self):
        return self.stack[len(self.stack) - 1][0]

    def min(self):
        return self.stack[len(self.stack) - 1][1]

    def size(self):
        return len(self.stack)


class Queue:
    def __init__(self):
        self.right_stack = Stack()
        self.left_stack = Stack()

    def push(self, element):
        self.left_stack.push(element)

    def pop(self):
        if not self.right_stack.size():
            while self.left_stack.size():
                self.right_stack.push(self.left_stack.peek())
                self.left_stack.pop()
        return self.right_stack.pop()

    def min(self):
        if not self.right_stack.size():
            while self.left_stack.size():
                self.right_stack.push(self.left_stack.peek())
                self.left_stack.pop()
        return self.right_stack.min()


main()
