# Many-time-pad-attack
- Idea:
    Vì c = x XOR k nên khi có các cipher text được enc bởi cùng một k thì ta có:
        c1 = x1 XOR k
        c2 = x2 XOR K
    => c1 XOR c2 = (x1 XOR k) XOR (x2 XOR k) = x1 XOR x2
  Vậy nên khi ta XOR 2 cipher text thì chúng tương đương với kết quả XOR 2 plain text => lấy c1 so lần lượt với tất cả các c còn lại tương đương với với lấy x1 so với lần lượt các x còn lại.
  Nhận thấy rằng khi XOR một dấu space ( hex là '20') với bất kỳ một chữ cái nào thì nó cũng ra 1 chữ cái, nên khi lấy x1 XOR với tất cả các x còn lại mà ở vị trí byte nào thường xuyên xuất hiện chữ cái (~ 70%) thì rất có thể chỗ đó là một dấu space. Tìm ra tất cả các vị trí có thể là dấu space của x thì ta có thể đoán ra ký hiệu tại vị trí đó của k vì ta đã có c. Làm lần lượt với tất cả các c ta sẽ đoán được đại khái k và từ đó tìm ra target nhờ XOR.
- Sẽ có những nhiễu loạn nhất định vì:
    Tỷ lệ 70% là đoán ra nhờ việc thử với nhiều tỷ lệ khác và thấy rằng tỷ lệ 70% đoán ra được nhiều ký tự của key nhất.
    Có những byte mà cả 10 x không chuỗi nào có ký hiệu space tại byte đó nên không có căn cứ để đoán ra ký hiệu key tại đó.
  
