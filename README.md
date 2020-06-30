# DatePickerRange
Element当type="daterange"的时候，选择器是第一次点选开始时间，第二次点选结束时间，而不是第一个选择器是开始，第二个选择器是结束。第一次用很容易去在第一个时间选择器里试点一下，然后再去在这第一个里选开始时间，结果就选择了一个时间范围。其实知道了使用方法之后还好。但是很多人用户表示莫名其妙不会用。
然后可以用两个type="date"的DatePicker实现类似type="daterange"的功能。第一个点几次都是开始，第二个点几次都是结束。开始时间里超过结束时间的不能选，结束时间里比开始时间还古老不能选。
使用：\<DatePickerRange :values="array" :inputWidth="150"/>
