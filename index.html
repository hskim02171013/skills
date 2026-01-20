import React, { useState, useEffect } from 'react';
import { ThumbsUp, MessageSquare, Trash2, Users, X, Check } from 'lucide-react';

const RestaurantVoteApp = () => {
  const [isLoggedIn, setIsLoggedIn] = useState(false);
  const [currentUser, setCurrentUser] = useState(null);
  const [loginName, setLoginName] = useState('');
  const [loginGrade, setLoginGrade] = useState('1');
  const [loginPassword, setLoginPassword] = useState('');
  
  const [mainTab, setMainTab] = useState('vote');
  const [mealTab, setMealTab] = useState('breakfast');
  
  const [votes, setVotes] = useState({});
  const [userVotes, setUserVotes] = useState({});
  const [comments, setComments] = useState({});
  const [confirmed, setConfirmed] = useState({});
  const [confirmedHistory, setConfirmedHistory] = useState([]);
  const [newComment, setNewComment] = useState({});
  const [showComments, setShowComments] = useState({});
  const [lastResetDate, setLastResetDate] = useState('');
  
  const [showAdminPanel, setShowAdminPanel] = useState(false);
  const [users, setUsers] = useState({});
  const [hasAdminAccess, setHasAdminAccess] = useState(false);

  const restaurantData = [
    { id: 1, name: '마미쿡', phone: '043-XXX-XXXX', categories: ['breakfast', 'dinner'] },
    { id: 2, name: '샌토락', phone: '043-XXX-XXXX', categories: ['breakfast'] },
    { id: 3, name: '한솥', phone: '043-XXX-XXXX', categories: ['lunch'] },
    { id: 4, name: '고향순대', phone: '043-XXX-XXXX', categories: ['dinner'] },
    { id: 5, name: '꼬막짬뽕', phone: '043-XXX-XXXX', categories: ['lunch', 'dinner'] },
    { id: 6, name: '밀리네', phone: '043-XXX-XXXX', categories: ['lunch', 'dinner'] },
    { id: 7, name: '보령식당', phone: '043-XXX-XXXX', categories: ['dinner'], special: true },
  ];

  const mealTabs = [
    { id: 'breakfast', label: '아침', icon: '🌅' },
    { id: 'lunch', label: '점심', icon: '🌞' },
    { id: 'dinner', label: '저녁', icon: '🌙' },
  ];

  useEffect(() => {
    checkSession();
    loadData();
    const adminAccess = localStorage.getItem('hasAdminAccess');
    if (adminAccess === 'true') {
      setHasAdminAccess(true);
    }
  }, []);

  useEffect(() => {
    if (lastResetDate) {
      checkDailyReset();
    }
  }, [lastResetDate]);

  useEffect(() => {
    if (currentUser) {
      checkYearlyGradeUpdate();
    }
  }, [currentUser]);

  const checkSession = () => {
    const savedUser = localStorage.getItem('currentUser');
    if (savedUser) {
      const user = JSON.parse(savedUser);
      setCurrentUser(user);
      setIsLoggedIn(true);
    }
  };

  const loadData = async () => {
    try {
      const votesData = await window.storage.get('votes', true);
      const userVotesData = await window.storage.get('user-votes', true);
      const commentsData = await window.storage.get('comments', true);
      const confirmedData = await window.storage.get('confirmed', true);
      const historyData = await window.storage.get('confirmed-history', true);
      const resetData = await window.storage.get('last-reset', true);
      const usersData = await window.storage.get('users', true);
      
      if (votesData) setVotes(JSON.parse(votesData.value));
      if (userVotesData) setUserVotes(JSON.parse(userVotesData.value));
      if (commentsData) setComments(JSON.parse(commentsData.value));
      if (confirmedData) setConfirmed(JSON.parse(confirmedData.value));
      if (historyData) setConfirmedHistory(JSON.parse(historyData.value));
      if (resetData) setLastResetDate(resetData.value);
      if (usersData) setUsers(JSON.parse(usersData.value));
    } catch (error) {
      console.log('데이터 로딩:', error);
    }
  };

  const saveData = async (type, data) => {
    try {
      await window.storage.set(type, typeof data === 'string' ? data : JSON.stringify(data), true);
    } catch (error) {
      console.error('저장 실패:', error);
    }
  };

  const checkDailyReset = () => {
    const today = new Date().toDateString();
    if (lastResetDate !== today) {
      const newHistory = [
        ...confirmedHistory,
        { date: lastResetDate, confirmed: { ...confirmed } }
      ].slice(-30);
      
      setConfirmedHistory(newHistory);
      saveData('confirmed-history', newHistory);
      
      setVotes({});
      setUserVotes({});
      setConfirmed({});
      setLastResetDate(today);
      saveData('votes', {});
      saveData('user-votes', {});
      saveData('confirmed', {});
      saveData('last-reset', today);
    }
  };

  const checkYearlyGradeUpdate = () => {
    const now = new Date();
    const currentYear = now.getFullYear();
    const userYear = currentUser.registeredYear || currentYear;
    
    if (currentYear > userYear && now.getMonth() === 0 && now.getDate() === 1) {
      const newGrade = Math.min(currentUser.grade + (currentYear - userYear), 4);
      const updatedUser = { ...currentUser, grade: newGrade, registeredYear: currentYear };
      setCurrentUser(updatedUser);
      localStorage.setItem('currentUser', JSON.stringify(updatedUser));
      
      const newUsers = { ...users, [currentUser.name]: updatedUser };
      setUsers(newUsers);
      saveData('users', newUsers);
    }
  };

  const handleLogin = () => {
    if (loginName.trim() === 'admin' && loginPassword === 'admin') {
      const adminUser = { name: 'admin', grade: 0, isAdmin: true, registeredYear: new Date().getFullYear() };
      setCurrentUser(adminUser);
      setIsLoggedIn(true);
      localStorage.setItem('currentUser', JSON.stringify(adminUser));
      localStorage.setItem('hasAdminAccess', 'true');
      setHasAdminAccess(true);
      return;
    }
    
    if (!loginName.trim()) return;
    
    const existingUser = users[loginName];
    if (existingUser) {
      setCurrentUser(existingUser);
      setIsLoggedIn(true);
      localStorage.setItem('currentUser', JSON.stringify(existingUser));
    } else {
      const newUser = {
        name: loginName,
        grade: parseInt(loginGrade),
        registeredYear: new Date().getFullYear()
      };
      const newUsers = { ...users, [loginName]: newUser };
      setUsers(newUsers);
      saveData('users', newUsers);
      setCurrentUser(newUser);
      setIsLoggedIn(true);
      localStorage.setItem('currentUser', JSON.stringify(newUser));
    }
  };

  const handleVote = (restaurantId) => {
    const userCurrentVote = userVotes[`${currentUser.name}-${mealTab}`];
    
    if (userCurrentVote === restaurantId) {
      const newVotes = { ...votes, [restaurantId]: Math.max((votes[restaurantId] || 0) - 1, 0) };
      const newUserVotes = { ...userVotes };
      delete newUserVotes[`${currentUser.name}-${mealTab}`];
      
      setVotes(newVotes);
      setUserVotes(newUserVotes);
      saveData('votes', newVotes);
      saveData('user-votes', newUserVotes);
      return;
    }
    
    if (userCurrentVote) {
      const newVotes = {
        ...votes,
        [userCurrentVote]: Math.max((votes[userCurrentVote] || 0) - 1, 0),
        [restaurantId]: (votes[restaurantId] || 0) + 1
      };
      const newUserVotes = {
        ...userVotes,
        [`${currentUser.name}-${mealTab}`]: restaurantId
      };
      
      setVotes(newVotes);
      setUserVotes(newUserVotes);
      saveData('votes', newVotes);
      saveData('user-votes', newUserVotes);
    } else {
      const newVotes = { ...votes, [restaurantId]: (votes[restaurantId] || 0) + 1 };
      const newUserVotes = { ...userVotes, [`${currentUser.name}-${mealTab}`]: restaurantId };
      
      setVotes(newVotes);
      setUserVotes(newUserVotes);
      saveData('votes', newVotes);
      saveData('user-votes', newUserVotes);
    }
  };

  const handleAddComment = (restaurantId) => {
    if (currentUser.isAdmin) return;
    if (!newComment[restaurantId]?.trim()) return;
    
    const timestamp = new Date().toLocaleString('ko-KR');
    const gradeLabel = currentUser.grade >= 4 ? '졸업자' : `${currentUser.grade}학년`;
    
    const newComments = {
      ...comments,
      [restaurantId]: [
        ...(comments[restaurantId] || []),
        {
          text: newComment[restaurantId],
          timestamp,
          author: currentUser.name,
          grade: gradeLabel
        }
      ]
    };
    setComments(newComments);
    saveData('comments', newComments);
    setNewComment({ ...newComment, [restaurantId]: '' });
  };

  const handleDeleteComment = (restaurantId, commentIndex) => {
    const newComments = {
      ...comments,
      [restaurantId]: comments[restaurantId].filter((_, idx) => idx !== commentIndex)
    };
    setComments(newComments);
    saveData('comments', newComments);
  };

  const handleConfirm = (mealType, restaurantId) => {
    const alreadyConfirmed = Object.entries(confirmed).find(
      ([key, value]) => key !== mealType && value === restaurantId
    );
    
    if (alreadyConfirmed) {
      alert('이 식당은 이미 다른 시간대에 확정되어 있습니다!');
      return;
    }
    
    const newConfirmed = { ...confirmed, [mealType]: restaurantId };
    setConfirmed(newConfirmed);
    saveData('confirmed', newConfirmed);
  };

  const handleDeleteUser = (username) => {
    const newUsers = { ...users };
    delete newUsers[username];
    setUsers(newUsers);
    saveData('users', newUsers);
  };

  const getGradeLabel = (grade) => {
    if (grade >= 4) return '졸업자';
    return `${grade}학년`;
  };

  const getRestaurantStatus = (restaurantId) => {
    if (confirmedHistory.length > 0) {
      const yesterday = confirmedHistory[confirmedHistory.length - 1];
      const yesterdayConfirmed = Object.values(yesterday.confirmed || {});
      if (yesterdayConfirmed.includes(restaurantId)) {
        return { isYesterday: true, daysAgo: 1 };
      }
    }
    
    for (let i = confirmedHistory.length - 1; i >= 0; i--) {
      const historyItem = confirmedHistory[i];
      const confirmedInHistory = Object.values(historyItem.confirmed || {});
      if (confirmedInHistory.includes(restaurantId)) {
        const daysAgo = confirmedHistory.length - i;
        return { isYesterday: false, daysAgo };
      }
    }
    
    return { isYesterday: false, daysAgo: null };
  };

  if (!isLoggedIn) {
    return (
      <div className="min-h-screen bg-gradient-to-br from-orange-400 to-yellow-400 flex items-center justify-center p-4">
        <div className="bg-white rounded-2xl shadow-2xl p-8 w-full max-w-md">
          <div className="text-center mb-8">
            <h1 className="text-4xl font-bold text-gray-800 mb-2">🍽️ 밥 투표</h1>
            <p className="text-gray-600">로그인하여 시작하세요</p>
          </div>
          
          <div className="space-y-4">
            <div>
              <label className="block text-sm font-semibold text-gray-700 mb-2">이름</label>
              <input
                type="text"
                value={loginName}
                onChange={(e) => setLoginName(e.target.value)}
                onKeyPress={(e) => e.key === 'Enter' && handleLogin()}
                placeholder="이름을 입력하세요"
                className="w-full px-4 py-3 border-2 border-gray-300 rounded-lg focus:outline-none focus:border-orange-500"
              />
            </div>
            
            {loginName === 'admin' ? (
              <div>
                <label className="block text-sm font-semibold text-gray-700 mb-2">비밀번호</label>
                <input
                  type="password"
                  value={loginPassword}
                  onChange={(e) => setLoginPassword(e.target.value)}
                  onKeyPress={(e) => e.key === 'Enter' && handleLogin()}
                  placeholder="비밀번호를 입력하세요"
                  className="w-full px-4 py-3 border-2 border-gray-300 rounded-lg focus:outline-none focus:border-orange-500"
                />
              </div>
            ) : (
              <div>
                <label className="block text-sm font-semibold text-gray-700 mb-2">학년</label>
                <select
                  value={loginGrade}
                  onChange={(e) => setLoginGrade(e.target.value)}
                  className="w-full px-4 py-3 border-2 border-gray-300 rounded-lg focus:outline-none focus:border-orange-500"
                >
                  <option value="1">1학년</option>
                  <option value="2">2학년</option>
                  <option value="3">3학년</option>
                </select>
              </div>
            )}
            
            <button
              onClick={handleLogin}
              className="w-full bg-gradient-to-r from-orange-500 to-yellow-500 text-white font-bold py-3 rounded-lg hover:from-orange-600 hover:to-yellow-600 transition-all"
            >
              시작하기
            </button>
          </div>
        </div>
      </div>
    );
  }

  const filteredRestaurants = restaurantData.filter(r => r.categories.includes(mealTab));

  return (
    <div className="min-h-screen bg-gradient-to-br from-orange-50 to-yellow-50 p-4">
      <div className="max-w-4xl mx-auto">
        <div className="bg-white rounded-2xl shadow-xl overflow-hidden">
          <div className="bg-gradient-to-r from-orange-500 to-yellow-500 p-6 text-white">
            <div className="flex justify-between items-center">
              <div>
                <h1 className="text-3xl font-bold">🍽️ 밥 투표</h1>
                <p className="mt-1 text-orange-100">
                  {currentUser.name} ({getGradeLabel(currentUser.grade)})
                </p>
              </div>
              <div className="flex gap-2">
                {currentUser.isAdmin && (
                  <button
                    onClick={() => setShowAdminPanel(!showAdminPanel)}
                    className="bg-white text-orange-600 px-4 py-2 rounded-lg font-semibold hover:bg-orange-100 transition-all"
                  >
                    관리자 패널
                  </button>
                )}
                {(currentUser.isAdmin || hasAdminAccess) && (
                  <button
                    onClick={() => {
                      localStorage.removeItem('currentUser');
                      setCurrentUser(null);
                      setIsLoggedIn(false);
                    }}
                    className="bg-red-500 text-white px-4 py-2 rounded-lg font-semibold hover:bg-red-600 transition-all"
                  >
                    로그아웃
                  </button>
                )}
              </div>
            </div>
          </div>

          {showAdminPanel && currentUser.isAdmin && (
            <div className="bg-gray-100 p-6 border-b">
              <h3 className="font-bold text-lg mb-4 flex items-center gap-2">
                <Users size={20} />
                사용자 관리
              </h3>
              <div className="space-y-2 max-h-60 overflow-y-auto">
                {Object.entries(users).map(([username, user]) => (
                  <div key={username} className="flex items-center justify-between bg-white p-3 rounded-lg">
                    <span className="font-medium">
                      {user.name} ({getGradeLabel(user.grade)})
                    </span>
                    <button
                      onClick={() => handleDeleteUser(username)}
                      className="text-red-600 hover:text-red-800"
                    >
                      <Trash2 size={18} />
                    </button>
                  </div>
                ))}
              </div>
            </div>
          )}

          <div className="flex border-b bg-gray-50">
            <button
              onClick={() => setMainTab('vote')}
              className={`flex-1 py-4 px-6 font-semibold transition-all ${
                mainTab === 'vote'
                  ? 'bg-white text-orange-600 border-b-4 border-orange-500'
                  : 'text-gray-500 hover:bg-gray-100'
              }`}
            >
              밥
            </button>
            <button
              onClick={() => setMainTab('confirmed')}
              className={`flex-1 py-4 px-6 font-semibold transition-all ${
                mainTab === 'confirmed'
                  ? 'bg-white text-orange-600 border-b-4 border-orange-500'
                  : 'text-gray-500 hover:bg-gray-100'
              }`}
            >
              확정
            </button>
          </div>

          {mainTab === 'vote' && (
            <>
              <div className="flex border-b bg-gray-50">
                {mealTabs.map(tab => (
                  <button
                    key={tab.id}
                    onClick={() => setMealTab(tab.id)}
                    className={`flex-1 py-3 px-4 font-semibold transition-all ${
                      mealTab === tab.id
                        ? 'bg-white text-orange-600 border-b-2 border-orange-500'
                        : 'text-gray-500 hover:bg-gray-100'
                    }`}
                  >
                    <span className="text-xl mr-1">{tab.icon}</span>
                    {tab.label}
                  </button>
                ))}
              </div>

              <div className="p-6">
                <div className="space-y-4">
                  {filteredRestaurants.map(restaurant => {
                    const userCurrentVote = userVotes[`${currentUser.name}-${mealTab}`];
                    const hasVoted = userCurrentVote === restaurant.id;
                    const status = getRestaurantStatus(restaurant.id);
                    const isOtherVoted = userCurrentVote && !hasVoted;
                    
                    return (
                      <div 
                        key={restaurant.id} 
                        className={`border-2 rounded-xl p-5 transition-all ${
                          isOtherVoted
                            ? 'bg-gray-100 border-gray-300 opacity-60'
                            : 'bg-white border-orange-200 hover:shadow-md'
                        }`}
                      >
                        <div className="flex items-start justify-between mb-3">
                          <div className="flex-1">
                            <h3 className="text-xl font-bold text-gray-800 flex items-center gap-2 flex-wrap">
                              {restaurant.name}
                              {status.isYesterday && (
                                <span className="text-sm text-gray-500 font-normal">
                                  (어제 먹었습니다)
                                </span>
                              )}
                              {restaurant.special && (
                                <span className="text-xs bg-purple-100 text-purple-700 px-2 py-1 rounded-full font-medium">
                                  특수
                                </span>
                              )}
                              {!status.isYesterday && status.daysAgo && status.daysAgo >= 3 && (
                                <span className="text-xs bg-blue-400 text-white px-2 py-1 rounded-full font-medium">
                                  {status.daysAgo}일 동안 먹지 않았습니다
                                </span>
                              )}
                            </h3>
                            <p className="text-sm text-gray-500 mt-1">📞 {restaurant.phone}</p>
                          </div>
                          
                          <button
                            onClick={() => handleVote(restaurant.id)}
                            className="flex items-center gap-2 px-4 py-2 rounded-lg font-semibold transition-all bg-orange-500 text-white hover:bg-orange-600 active:scale-95"
                          >
                            <ThumbsUp size={18} />
                            <span>{votes[restaurant.id] || 0}</span>
                          </button>
                        </div>

                        <button
                          onClick={() => setShowComments({
                            ...showComments,
                            [restaurant.id]: !showComments[restaurant.id]
                          })}
                          className="flex items-center gap-2 text-sm text-orange-600 hover:text-orange-700 font-medium mb-3"
                        >
                          <MessageSquare size={16} />
                          코멘트 {comments[restaurant.id]?.length || 0}개
                        </button>

                        {showComments[restaurant.id] && (
                          <div className="mt-3 space-y-3">
                            {comments[restaurant.id]?.map((comment, idx) => (
                              <div key={idx} className="bg-orange-50 p-3 rounded-lg">
                                <div className="flex justify-between items-start mb-1">
                                  <div className="flex items-center gap-2">
                                    <span className="font-semibold text-gray-800">{comment.author}</span>
                                    <span className={`text-xs px-2 py-1 rounded-full ${
                                      comment.grade === '졸업자'
                                        ? 'bg-purple-100 text-purple-700'
                                        : 'bg-blue-100 text-blue-700'
                                    }`}>
                                      {comment.grade}
                                    </span>
                                  </div>
                                  {currentUser.isAdmin && (
                                    <button
                                      onClick={() => handleDeleteComment(restaurant.id, idx)}
                                      className="text-red-500 hover:text-red-700"
                                    >
                                      <Trash2 size={14} />
                                    </button>
                                  )}
                                </div>
                                <p className="text-gray-800">{comment.text}</p>
                                <p className="text-xs text-gray-500 mt-1">{comment.timestamp}</p>
                              </div>
                            ))}
                            
                            {!currentUser.isAdmin && (
                              <div className="flex gap-2 mt-3">
                                <input
                                  type="text"
                                  value={newComment[restaurant.id] || ''}
                                  onChange={(e) => setNewComment({
                                    ...newComment,
                                    [restaurant.id]: e.target.value
                                  })}
                                  onKeyPress={(e) => e.key === 'Enter' && handleAddComment(restaurant.id)}
                                  placeholder="코멘트를 남겨보세요..."
                                  className="flex-1 px-4 py-2 border-2 border-orange-200 rounded-lg focus:outline-none focus:border-orange-400"
                                />
                                <button
                                  onClick={() => handleAddComment(restaurant.id)}
                                  className="px-5 py-2 bg-orange-500 text-white rounded-lg font-semibold hover:bg-orange-600 transition-all"
                                >
                                  등록
                                </button>
                              </div>
                            )}
                          </div>
                        )}
                      </div>
                    );
                  })}
                </div>
              </div>
            </>
          )}

          {mainTab === 'confirmed' && (
            <div className="p-6">
              {mealTabs.map(tab => {
                const confirmedRestaurantId = confirmed[tab.id];
                const confirmedRestaurant = restaurantData.find(r => r.id === confirmedRestaurantId);
                const mealRestaurants = restaurantData.filter(r => r.categories.includes(tab.id));
                const alreadyConfirmedIds = Object.values(confirmed).filter(id => id !== confirmedRestaurantId);
                
                return (
                  <div key={tab.id} className="mb-6 border-2 border-orange-200 rounded-xl p-5 bg-white">
                    <h3 className="text-xl font-bold text-gray-800 mb-4 flex items-center gap-2">
                      <span className="text-2xl">{tab.icon}</span>
                      {tab.label}
                    </h3>
                    
                    {confirmedRestaurant ? (
                      <div className="bg-green-50 border-2 border-green-400 rounded-lg p-4">
                        <div className="flex items-center justify-between">
                          <div>
                            <h4 className="text-2xl font-bold text-green-800 flex items-center gap-2">
                              <Check className="text-green-600" size={24} />
                              {confirmedRestaurant.name}
                            </h4>
                            <p className="text-sm text-green-700 mt-1">📞 {confirmedRestaurant.phone}</p>
                          </div>
                          {currentUser.isAdmin && (
                            <button
                              onClick={() => handleConfirm(tab.id, null)}
                              className="text-red-500 hover:text-red-700"
                            >
                              <X size={24} />
                            </button>
                          )}
                        </div>
                      </div>
                    ) : (
                      <div className="text-center py-8 text-gray-500">
                        {currentUser.isAdmin ? (
                          <div>
                            <p className="mb-4">확정된 식당이 없습니다. 선택해주세요:</p>
                            <div className="space-y-2">
                              {mealRestaurants.map(restaurant => {
                                const isAlreadyConfirmed = alreadyConfirmedIds.includes(restaurant.id);
                                return (
                                  <button
                                    key={restaurant.id}
                                    onClick={() => handleConfirm(tab.id, restaurant.id)}
                                    disabled={isAlreadyConfirmed}
                                    className={`w-full py-2 px-4 rounded-lg transition-all font-semibold ${
                                      isAlreadyConfirmed
                                        ? 'bg-gray-300 text-gray-500 cursor-not-allowed'
                                        : 'bg-orange-500 text-white hover:bg-orange-600'
                                    }`}
                                  >
                                    {restaurant.name} 확정하기
                                    {isAlreadyConfirmed && ' (다른 시간대에 확정됨)'}
                                  </button>
                                );
                              })}
                            </div>
                          </div>
                        ) : (
                          <p>아직 확정된 식당이 없습니다.</p>
                        )}
                      </div>
                    )}
                  </div>
                );
              })}
            </div>
          )}
        </div>
      </div>
    </div>
  );
};

export default RestaurantVoteApp;