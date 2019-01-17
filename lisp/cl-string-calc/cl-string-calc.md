
  ������ Clojure - emacs �� �̿��� [String calculator katacast]�� ���ԵǾ��� Common Lisp���� �ѹ� �غ��ڴ� ������ emacs�� �Ѽ� �ۼ��غ��Ҵ�.

 �ϴ� tddȯ���� �����ϰ��� �Ҷ� ������ ���� �� ����� �־� ã�ƺ��� ã���� �ϴ°� �־���. [��α�][lisp-unit-blog]�� ���� �ֵ��� [lisp-unit]�� ��� ����� �°� �ؽ�Ʈ�� �ʷ�//�������� ����� �ִ� ���� �־���.

 ������Ʈ �����ϴ� ��Ű���� [quickproject]�� [cl-project]�� ������ tddȯ�濡�� [cl-test-more]�� �̿��ϴ� cl-project�� ����ϴ°� ����, �� ��α׿��� [slime-lispunit.el]������ �ٿ� ���� ��, cl-test-more������ �°� ���ƴ�. �ؽ�Ʈ�� ������ ������ ��� vimeo�� ���� ������ó�� �����θ� �ٲ�� �����ϰ� �׽�Ʈ�� ������ �� �־���.

 �ϴ� Common Lisp�� �ϼ��� ������Ʈ�� [�̰�][netpyoung's string-calc]���� Ȯ���� �� �ִ�.

 �� �ۼ��� �׽�Ʈ ����� �ٸ� ���ۿ� ��½�Ű�� ����� ������ �ٽ� .el ������ ������ [popwin-el]�̶��� �־� �ѹ� �̰� �Ẹ�Ҵ�. �ۼ��� .el������ [�̰�][netpyoung's cl-test-more.el]���� ���� �� �ִ�.


 Ű���� ������ ����

```elisp
;; Keys

(slime-define-keys slime-mode-map
    ((kbd "C-t C-j") 'tst:switch-test<->source)
    ((kbd "C-t C-o") 'tst:on-off-test-result-popup)
    ((kbd "C-t C-t") 'tst:run-test)
    ((kbd "C-t C-e") 'tst:remove-test)
    ((kbd "C-t C-a") 'tst:run-all-tests)
    ((kbd "C-t C-c") 'tst:clear-all-tests)
    ((kbd "C-t C-r") 'tst:repeat-last-test))
```

��ũ�� ��
 ![cl-test-more_pass-mode-line](../imgs/cl-test-more_pass-mode-line.png)
 ![cl-test-more_pass-popup-result.png](../imgs/cl-test-more_pass-popup-result.png)
 ![cl-test-more_fail-mode-line.jpg](../imgs/cl-test-more_fail-mode-line.jpg)
 ![cl-test-more_fail-popup-result.png](../imgs/cl-test-more_fail-popup-result.png)


 [String calculator katacast]: http://vimeo.com/9350864
 [lisp-unit-blog]: http://cons.pulp.se/post/522988094/introducing-slime-lispunit
 [lisp-unit]: https://github.com/OdonataResearchLLC/lisp-unit
 [quickproject]: https://github.com/xach/quickproject
 [cl-project]: https://github.com/fukamachi/cl-project
 [cl-test-more]: https://github.com/fukamachi/cl-test-more
 [slime-lispunit.el]: https://github.com/johanlindberg/slime/blob/master/contrib/slime-lispunit.el
 [netpyoung's string-calc]: https://github.com/netpyoung/Practice/tree/master/Lisp/string-calc
 [popwin-el]: https://github.com/m2ym/popwin-el
 [netpyoung's cl-test-more.el]: https://github.com/netpyoung/emacs-config/blob/master/cl-test-more/cl-test-more.el