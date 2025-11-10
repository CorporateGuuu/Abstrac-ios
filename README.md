# Dare App - Firebase Setup & Testing Guide

## Firestore Collections

### Skins Collection

Example skin documents:

#### Document: `lv_premium`
```json
{
  "name": "LV",
  "price": 500,
  "frameLayout": "lv",
  "textColor": { "red": 1.0, "green": 0.84, "blue": 0.0, "alpha": 1.0 },
  "backgroundImage": "gs://dareme-app.appspot.com/skins/lv_bg.jpg",
  "isPremium": true
}
```

#### Document: `empty_free`
```json
{
  "name": "Default",
  "price": 0,
  "frameLayout": "empty",
  "textColor": { "red": 1.0, "green": 1.0, "blue": 1.0, "alpha": 1.0 },
  "backgroundImage": null,
  "isPremium": false
}
```

## Seasonal Skins

### Winter 2025 Collection

#### Document: `frostbite_sss` (Seasonal SSS)
```json
{
  "name": "Frostbite",
  "price": 2000,
  "tier": "SSS",
  "frameLayout": "frostbite",
  "textColor": { "red": 0.8, "green": 0.9, "blue": 1.0, "alpha": 1.0 },
  "backgroundImage": "gs://dareme-app.appspot.com/skins/frostbite_bg.jpg",
  "season": "winter2025",
  "availableUntil": "2026-01-31T23:59:59Z"
}
```

### Seasonal Features
- **Limited Time**: `availableUntil` field controls availability
- **Season Tags**: `season` field for categorization
- **Premium Pricing**: Seasonal skins often have higher value
- **Unique Themes**: Winter, Summer, Halloween, etc.


# Test functions in shell
firebase functions:shell

# Example: Test moderateVote function
moderateVote({
  dareId: "test-dare-id",
  isUpvote: true
})
```

### Manual Testing Checklist

- [ ] Vote on dare → UI updates immediately
- [ ] Vote count displays correctly
- [ ] Offline voting queues properly
- [ ] Reconnection syncs queued votes
- [ ] Rate limiting prevents spam
- [ ] Self-vote prevention works
- [ ] Authentication required for voting
- [ ] Firestore logs show successful processing
- [ ] Error messages display for invalid votes

## Troubleshooting

### Common Issues

**Functions not deploying**:
```bash
firebase functions:list  # Check if deployed
firebase functions:log   # Check for errors
```

**Votes not syncing**:
- Check internet connection
- Verify Firebase configuration
- Check device logs for network errors

**Authentication errors**:
- Ensure user is logged in
- Check Firebase Auth configuration
- Verify security rules allow access

### Debug Commands

```bash
# View all function logs
firebase functions:log

# View specific function logs
firebase functions:log --only moderateVote

# Check function status
firebase functions:list

# Test security rules
firebase firestore:indexes  # Check if rules deployed
# Abstrac-ios
# Abstrac-ios
