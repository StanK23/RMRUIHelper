## RMRUIHelper
Это pod, который содержит вспомогательные сущности и базовые реализации для наиболее часто используемых компонентов в ходе разработки iOS проектов.

В описании опущены детали реализации, а так же классы, которые на данный момент считаются устаревшими или некорректно отрабатывают на актуальных версиях ОС.

### NSLayoutConstraint+RMRHelper
Содержит вспомогательные методы для работы с объектами NSLayoutConstraint из кода. Например — установка константы для всех NSLayoutConstraint в массиве или подсчёт суммы значений constant*multiplier.

### NSString+RMRHelper
Содержит вспомогательные методы для работы со строками. Например — метод который возвращает YES, если строка является адресом электронной почты.

### NSString+RMRMoneyFormatting
Содержит вспомогательные методы для форматирования денежных значений в человекочитаемый формат.

### RMRActionSheet
Пример реализации кастомного Action Sheet на основе RMRModalView.

### RMRAddressBookPhoneHelper*
Вспомогательная сущность, которая упрощает работу с адресной книгой пользователя для выбора номера телефона.
*Реализация возможно неактуальна для версии ОС >= 8.0

### RMRAlertView
Пример реализации кастомного Alert View на основе RMRModalView.

### RMRBarsHelper
Содержит реализацию UI_APPEARANCE_SELECTOR для свойства Translucency у UINavigationBar, UITabBar, UISearchBar, UIToolbar.

### RMRBaseLabel
Базовый класс для Label с установкой кастомного шрифта и отрисовкой на холсте Interface Builder. Наследники должны переопределить метод + (UIFont *)rmr_font для установки шрифта при инициализации объекта. Для отрисовки в Interface Builder необходимо указать IBDesignable.

### RMRButton
Базовый класс для стилизации UIButton готовый для типовых сценариев RedMadRobot. 
Поддерживает IBDesignable.
Для стилизации необходимо переопределить метод + (void)rmr_prepareAppearance:(RMRButton *)button.

### RMRGradientLayer
Реализация Layer с простым градиентом в два цвета.

### RMRImage.swift
Содержит extension с вспомогательными методами:
— метод экземпляра, для получения изображения перекрашенного в указанный цвет
— метод класса, для получения изображения по имени, перекрашенного в указанный цвет

### RMRImageView
В iOS 7 и iOS 8 отрисовка изображений в UIImageView из файлов Interface Builder сломана и работает через раз. Изображение либо не получает верный rendering mode (iOS 7), либо не устанавливает tintColor (iOS 8). Этот класс обходит проблему.
Так же класс добавляет отрисовку изображения в tintColor в Interface Builder.
### RMRMessagesHelper
Вспомогательная сущность для упрощения работы с MessageUI. Оборачивает отправку сообщений и писем в единый интерфейс.

### RMRModalViewsController
Сущность, которая управляет отображением view в модальном режиме. View добавляются в window выше status bar. Это позволяет реализовать модальные индикаторы загрузки, кастомные alert view или action sheet. Добавляемые view должны реализовать протокол RMRModalView.

### RMRNavigationControllerDelegate
Вспомогательная сущность, которая реализует протокол UINavigationControllerDelegate с целью скрыть title у back button. Создана для использования в Interface Builder. 
Как использовать:
— В navigation controller на storyboard добавляем object и указываем в качестве класса RMRNavigationControllerDelegate. 
— Устанавливаем этот объект делегатом navigation controller.
— Вы великолепны.

### RMRRoundView
Просто круглая view. Subviews по умолчанию не обрезаются (self.clipsToBounds == NO).

### RMRSeparatorSizeConstraint
NSLayoutConstraint, который после загрузки из nib устанавливает своё свойство constant в значение 0.5f.*
*Вероятно требуется доработка под iPhone 6/s Plus.

### RMRSubtitleButton
Реализация RMRButton с подзаголовком. Поддерживает IBDesignable и IBInspectable.

### RMRTableView
В реализацию зашита логика с автоматической загрузкой и регистрацией в таблице ячеек в следующем порядке:
— если в bundle существует nib с именем соответствующим cell identifier, то он будет зарегистрирован
— если существует класс с именем соответствующем cell identifier,
 то он будет зарегистрирован
— если ни одно из условий не выполнено, будет брошено исключение
Немного шалит при работе из Swift.

### RMRTouchIdHelper
Вспомогательная сущность для упрощения работы с Touch ID. Содержит два метода:
— метод для определения состояния Touch ID — включен (в принципе доступен на устройстве) / выключен (или на устройстве вообще нет Touch ID)
— метод для авторизации пользователя. В качестве параметра принимает блок, который будет вызван в случае положительного или отрицательного результата.

### RMRXibViewContainer
Экспериментальная реализация контейнера для view реализованных в отдельном xib-файле. Как это работает:
— реализуем view в xib-файле
— добавляем на сцену storyboard view
— указываем в качестве класса RMRXibViewContainer
— указываем в viewClass (поддерживает IBInspectable) класс view из xib
Класс из xib будет отрисовываться на сцене Interface Builder.
Из минусов — view, описанная в xib, в рантайме будет доступна только через свойство subView у RMRXibViewContainer.

### UIButton+RMRHelper
Содержит реализацию UI_APPEARANCE_SELECTOR для установки шрифта для title кнопки.

### UIColor+RMRHelper
Содержит вспомогательные методы для работы с цветами:
— метод для получения цвета по значению 0.0 - 255.0
— метод для получения цвета на x% темнее заданного
— метод для получения цвета на x% светлее заданного

### UIImage+RMRHelper
Содержит вспомогательные методы для отрисовки изображений к стилизованным контролам. Смотрите заголовочный файл, там всё описано в комментариях.

### UINib+RMRHelper
Содержит метод для загрузки nib из bundle + (UINib *)RMR_nibWithNibName:(NSString *)name bundle:(NSBundle *)bundleOrNilВ отличие от метода SDK, отрабатывает верно и если nib с указанным именем не существует, возвращает nil. 

### UIView+RMRHelper
Содержит метод для загрузки полностью проинициализированной view из xib-файла и упрощенный метод для найстройки паралакса.

### WindowHelper
Содержит extension с методом для смены root view controller с анимацией.

### UIColor+HEX
Содержит extension с инициализатором UIColor из HEX RGB формата.

### ProgressView
Простая реализация кастомизируемого и масштабируемого view для отображения прогресса.