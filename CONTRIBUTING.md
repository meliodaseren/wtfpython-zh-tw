* 歡迎為本項目提供幫助。

* 本項目是以案例為單位提交的 commit, 如果您覺得我的翻譯有問題或看不懂的時候，打開 commit 記錄找到對應的例子就可以快速獲取文章的中英文對照。

* 您可以隨意開一個 issue 或者 pull requests 與我討論你覺得有問題的翻譯，請不要有任何顧慮。畢竟討論出真知。

* 如果你有什麽新的 Python 的有趣案例想與大家分享，優先推薦你提交給[原項目](https://github.com/satwikkansal/wtfpython/)。當然也可以直接提交給本項目。

* 為了保持本項目 commit 記錄能持續以案例為單位，當您的修改建議被採納時，我可能無法直接將您的 pull requests merge 進來。這點希望您能諒解。

* 我會將您的 GitHub 帳號加入[貢獻列表](https://github.com/meliodaseren/wtfpython-cn/blob/master/CONTRIBUTORS.md)中，同時會在相關的 issue 或 pull requests 中通知您。

您可以使用一下模板在原項目添加案例：

    ### ▶ Some fancy Title *
    The asterisk at the end of the title indicates the example was not present in the first release and has been recently added.

    ```py
    # Setting up the code.
    # Preparation for the magic...
    ```

    **Output (Python version):**
    ```py
    >>> triggering_statement
    Probably unexpected output
    ```
    (Optional): One line describing the unexpected output.

    #### 💡 Explanation:
    * Brief explanation of what's happening and why is it happening.
      ```py
      Setting up examples for clarification (if necessary)
      ```
      **Outupt:**
      ```py
      >>> trigger # some example that makes it easy to unveil the magic
      # some justified output
      ```
    ```